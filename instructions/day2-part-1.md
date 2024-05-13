## 1 - Bootstrap OpenHIM package
Like the previous reverse-proxy package bootstrap run the command `instant-linux package generate`
- Package name: openhim
- Name of package: OpenHIM training (not that important though)
- Docker image: jembi/openhim-core
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no

## 1.2 - Update the compose file to add the missing OpenHIM dependencies
Since the platform CLI cannot generate composite compose files we will need to manually update the compose file it generated to have OpenHIM console and Mongodb. You can use the [OpenHIM docs compose file](http://openhim.org/docs/getting-started/prerequisites/) as a reference. 

1. Rename compose service name from openhim to openhim-core
4. Add mongodb as a service to `docker-compose.yml` (make sure to define a volume)
```yaml
    mongodb: 
      image: mongo:4.0
      volumes:
        - "mongo-data:/data/db"

  volumes:
    mongo-data:
```
5. Add the environment variables for openhim-core in `package-metadata.json`
```json
  "environmentVariables": {
      "MONGO_URL": "mongodb://mongodb/openhim",
      "MONGO_ATNAURL": "mongodb://mongodb/openhim",
  }
```
6. Pass the environment variables defined to openhim-core service in the compose file.
```yaml
    environment:
      - mongo_url=${MONGO_URL}
      - mongo_atnaUrl=${MONGO_ATNAURL}
      - api_authenticationTypes=["token", "basic", "openid", "local"]
```
7. Add openhim-console service to compose file

## 1.3 - Update swarm.sh from bootstrap to working code
Like with the reverse-proxy package setup we will need to change the generated swarm.sh file to pass in the stack to the relevant function calls.
1. Add a new variable declaration near the top of the file (line 8)
```sh
...
declare SERVICE_NAMES=()
declare STACK="openhim" 
```
2. Update the `docker::deploy_service` function call to include the stack and the base compose-file and remove the reference to dev_compose (line ~48)
```sh
...
docker::deploy_service "$STACK" "${COMPOSE_FILE_PATH}" "docker-compose.yml"
```
3. Remove the call to `docker::deploy_sanity` just under the call to `deploy_service` since `deploy_service` includes a sanity check in it now.
4. Remove references to dev_compose variables
```sh
  local package_dev_compose_filename=""
  if [[ "${MODE}" == "dev" ]]; then
    log info "Running package in DEV mode"
    package_dev_compose_filename="docker-compose.dev.yml"

  # turns into:
  if [[ "${MODE}" == "dev" ]]; then
    log info "Running package in DEV mode"
```
5. Update `destroy_package` function to replace the `service_destroy` function call to `stack_destory` instead (line ~55)
```sh
docker::service_destroy "${SERVICE_NAMES[@]}" # turns into
docker::stack_destroy $STACK
```

## 2 - Update nginx ports + config
Since openhim binds port 8080 we now need to change the nginx port bindings. We can also remove the static html server and add the OpenHIM configs.
1. Update port binding from 8080 to 80 in `reverse-proxy/docker-compose.dev.yml`.
2. Bind port 80 to openhim-console
```conf
  server {
    listen       80;
    location / {
        resolver    127.0.0.11 valid=30s;
        proxy_pass  http://openhim-console:80;
    }
  }
```
> Instructor Aid: You might need to explain to them the first docker service config so they have a general idea on how to proxy pass a request to a docker service. The most important part is setting the `resolver` to the docker DNS, otherwise it will be unable to resolve the service names.
3. Bind port 5001 to openhim-core
```conf
  server {
    listen                5001;
    location / {
        resolver          127.0.0.11 valid=30s;
        proxy_pass        http://openhim-core:5001;
    }
  }
```
4. Bind port 5000 to openhim-core
```conf
  server {
    listen                5000;
    location / {
        resolver          127.0.0.11 valid=30s;
        proxy_pass        http://openhim-core:5000;
    }
  }
```
5. Add ports 5001 and 5000 to the reverse-proxy dev file.
6. Add a stream section to nginx and bind it to port 8080 (see the nginx config comment for more info why it is a stream)
```conf
  stream {
    server {
      listen      8080;
      resolver    127.0.0.11 valid=30s;
      proxy_pass  openhim-core:8080;
    }
  }
```
7. Add ports 8080 to reverse-proxy dev file.

## 3 - Add reverse-proxy as a dependency to openhim
Under the `package-metadata.json` file add the name of the nginx package we defined `reverse-proxy` for this training reference.
```json
  "dependencies": ["reverse-proxy"],
```

## 4 - Create an nginx network
Since openhim and nginx are both deployed into their own stack, they currently have no way of talking to each other. Therefore, we need to add a network definition to `reverse-proxy/docker-compose.yml` and then attach to that network in `openhim/docker-compose.yml` (only openhim-core and openhim-console).
```yaml (reverse-proxy/docker-compose.yml)
  reverse-proxy:
    networks:
      public:

  networks:
    public:
      name: reverse-proxy_public
      external: true
```
```yaml (openhim/docker-compose.yml)
  openhim-core:
    networks:
        reverse-proxy:
  
  openhim-console:
    networks:
      reverse-proxy:
  
  networks:
    reverse-proxy:
      name: reverse-proxy_public
      external: true
```

## 5 - Create the openhim default network
Since we don't want to attach the mongodb to the reverse-proxy network we need to define a default network and add it to every service in the openhim compose file. Since nothing will ever attach to it, it is isolated to openhim and does not need to be external as a result. There is also no need to attach mongodb to this default network since that is the default behavior docker provides when deploying services into a stack.
```yaml
  openhim-core:
    networks:
      reverse-proxy:
      default:

  openhim-console:
    networks:
      reverse-proxy:
      default:

  networks:
    reverse-proxy:
      name: reverse-proxy_public
      external: true
    default:
```


## 6 - Add openhim package to project file
We still need to add the new openhim package we generated to the `config.yaml` project file otherwise the CLI will have no knowledge of it.
```yaml
  packages:
      - reverse-proxy
      - openhim
```

## 7 - Build the image + test changes
Run the `build-image.sh` then `instant-linux package init -n openhim --dev`. Since we added reverse-proxy as a dependency to openhim we do not need to specify reverse-proxy.
1. Open localhost (since we bound openhim-console in nginx to port 80).
2. Check that we see the normal openhim login screen
3. Login
  - username: root@openhim.org
  - password: openhim-password
4. Update password and see that it all looks right

## 8 - (Optional) Cleanup
Run `instant-linux package remove -n openhim` to clear up any state we have if you wish. This will reset the openhim password you set though and will have to login with `openhim-password` again so not a necessary step.

## 9 - Bootstrap Hapi Fhir package
Run the command `instant-linux package generate`
- Package name: hapi-fhir
- Name of package: HAPI FHIR training (not that important though)
- Docker image: hapiproject/hapi
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: yes with port 8080 and 3447 (important to specify a different target port otherwise will conflict with openhim-core)

## 9.1 - Add a volume to hapi fhir
Following the docs on [hapi fhir docker page](https://hub.docker.com/r/hapiproject/hapi) the only thing you'd need to do to get hapi-fhir up and running is to attach a volume. No need to define a database as a backing.
```yaml
services:
  hapi-fhir:
    image: hapiproject/hapi
    volumes:
      - "hapi-data:/data/hapi"

volumes:
  hapi-data:
```

## 9.2 - Add stack name to swarm.sh + updates
Like before we need to:
1. Declare a stack variable
2. Update the service deploy function (add stack + base compose file) and remove sanity call
3. Replace the function in destroy function to call stack_destroy

## 9.3 - Add package to config.yaml project file

## 10 - Build image + test changes
1. Run `build-image.sh` and then bring up the two packages `instant-linux package init -n reverse-proxy -n hapi-fhir --dev`
2. Navigate to localhost:3447 and you should see the hapi-fhir landing page.
3. Post a bundle to localhost:3447
4. Use the hapi-fhir UI to check that the data was indeed created.

## 11 - Cleanup
Run the command `instant-linux project destroy` to clear up and finish the exercise.
