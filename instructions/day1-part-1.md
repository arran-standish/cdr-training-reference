## Starting off
Before you can do anything you need to get the instant openhie binary. I provided a script similar to the one in platform that will download the linux based one and update its access modifier to mark it as an executable.

> Instruction aid: they can go directly to the release page in github and manually download the file they need https://github.com/openhie/instant-v2/releases they'll just need to manually run chmod + x file to make it executalbe.


## 1 - Bootstrap the project
Run the command `instant-linux project generate`
- Name of project: anything you want
- Docker image: jembi/cdr-training (can also be anything you want since we'll need to define a Docker image anyway)
- Log path: default is fine
- No
- No
> Instruction aid: after the cli finishes generating the config.yaml file it will have two sections with empty {} in them, they should remove them otherwise it will cause issues (these bracers are placeholders for the two questions we answered no to).

## 2 - Create the Dockerfile
Before we'll be able to do anything with the package we create we will need to bundle them into the image that config.yaml references. You will need to inherit from `openhie/package-base:2.2.0` but the utils scripts has dependencies on jq, yq and envsubst so need to add these into the image (should be moved into package-base though).
> Instruction aid: This is not really something they will be able to figure out themsevles really, so it would be best to demo the Dockerfile and have them copy it onto their own setup.

## 3.1 - Bootstrap the package
Run the command `instant-linux package generate`.
- Package name: reverse-proxy
- Name of package: Reverse Proxy (not that important though)
- Docker image: nginx:stable
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: yes with port 8080 and 8080

### 3.2 - Add the package to the config.yaml
You now need to add your package to the list of packages that exist in config.yaml. So open config.yaml and replace `<<package-id>>` with `reverse-proxy` (or whatever you used for the name).

### 3.3 - Add the stack name to the swarm.sh
Since the current cli generation logic does not cater for stacks properly we need to manually update it, otherwise the calls will not work.

> Be sure to raise this to them as well and maybe even demo it the first time they generate a package since it is certainly not intuitive and they will not know what calls to change.

1. Add a new variable declaration near the top of the file (line 8)
```sh
...
declare SERVICE_NAMES=()
declare STACK="reverse-proxy" 
```
2. Update the `docker::deploy_service` function call to include the stack and the base compose-file (line ~48)
```sh
...
docker::deploy_service "$STACK" "${COMPOSE_FILE_PATH}" "docker-compose.yml" "$package_dev_compose_filename"
```
3. Remove the call to `docker::deploy_sanity` just under the call to `deploy_service` since `deploy_service` includes a sanity check in it now.
4. Update `destroy_package` function to replace the `service_destroy` function call to `stack_destory` instead (line ~55)
```sh
docker::service_destroy "${SERVICE_NAMES[@]}" # turns into
docker::stack_destroy $STACK
```
