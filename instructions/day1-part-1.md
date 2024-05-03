## Starting off
Before you can do anything you need to get the instant openhie binary. I provided a script similar to the one in platform that will download the linux based one and update its access modifier to mark it as an executable.

> Instruction aid: they can go directly to the release page in github and manually download the file they need https://github.com/openhie/instant-v2/releases they'll just need to manually run chmod + x file to make it executalbe.


## 1 - Bootstrap the project
Run the command `instant-linux project generate` choose the defaults for everything, but select no for both option when presented.

> Instruction aid: after the cli finishes generating the config.yaml file it will have two sections with empty {} in them, they should remove them otherwise it will cause issues (these bracers are placeholders for the two questions we answered no to). 

## 2.1 - Bootstrap the package
Run the command `instant-linux package generate`.
- Package name: reverse-proxy
- Name of package: Reverse Proxy (not that important though)
- Docker image: nginx:stable
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: yes with port 8080 and 8080

### 2.2 - Add the package to the config.yaml
You now need to add your package to the list of packages that exist in config.yaml. So open config.yaml and replace `<<package-id>>` with `reverse-proxy` (or whatever you used for the name).