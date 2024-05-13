# Elasticsearch Setup

## 1 - Bootstrap Elasticsearch package
Like the previous reverse-proxy package bootstrap run the command `instant-linux package generate`
- Package name: elasticsearch
- Name of package: Elasticsearch training (not that important though)
- Docker image: docker.elastic.co/elasticsearch/elasticsearch:7.13.0
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no
> Instructor Aid: They will need to use version 7 of Elastic, as that is the sdk version that the mapper consumer uses. So if you try and use the latest version (8.x) it will fail.

## 2 - Update the compose file to add required environment variables and volumes
The official Elasticsearch docs for setting up elastic search within docker is quite invovled as it sets up SSL as part of the process. 

1. Set environment variables
```yaml
    environment:
      xpack.security.enabled: "false" # makes sure we do not need to setup ssl
      discovery.type: "single-node" # required otherwise elastic will seek out other nodes and fail
      ES_ELASTIC: ${ES_ELASTIC} # set the password elastic uses
```
2. Create a volume:
```yaml
service:
  elasticsearch:
    volumes:
      - es-data:/usr/share/elasticsearch/data # important to bind the volume to the correct path for elastic

volumes:
  es-data:
```

## 3 - Create a default environment variable for ES_ELASTIC
Open up package-metadata.json and add an entry for the environment variable
```json
  "environmentVariables": {
    "ES_ELASTIC": "dev_password_only"
  }
```

## 4 - Make necessary changes to swarm.sh
1. Add stack variable
2. Remove sanity check + pass stack and compose file to deploy
3. Use stack destroy instead
4. Remove references to dev compose file

## 5 - Add elasticsearch to the project config.yaml file

## 6 - Add elasticsearch and kafka-mapping-consumer to the profile
Since we now have elastic, we have all the tools required to have the mapping consumer project running. So we can add it to the profile as well to make deployments easier.

## 7 - Make any necessary changes to the mapping consumer project
Just make sure that all environment variables reference the name chosen for the elasticsearch package, and that the name in the depedency list matches correctly. Or if they haven't already setup elasticsearch on the mapping-consumer project, now is the time.

## 8 - Create an elasticsearch network
Before the mapping-consumer project will be able to connect to elastic, it will have to be on the same network as it. Therefore, we need to create an elasticsearch network and attach the mapping-consumer service to it.
```yaml (elasticsearch/docker-compose.yml)
services:  
  elasticsearch:
    networks:
      public:

networks:
  public:
    name: elasticsearch_public
    external: true
```
```yaml (kafka-mapping-consumer/docker-compose.yml)
services:
  kafka-mapping-consumer:
    networks:
      kafka:
      elasticsearch: # new

networks:
  kafka:
    name: kafka_public
    external: true
  elasticsearch: # new
    name: elasticsearch_public
    external: true
```

# Kibana Setup

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