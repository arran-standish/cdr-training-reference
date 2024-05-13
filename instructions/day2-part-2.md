# Kafka Setup

## 1 - Bootstrap Kafka package
Run the command `instant-linux package generate`
- Package name: kafka
- Name of package: Kafka training (not that important though)
- Docker image: apache/kafka
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no

## 2 - Add environment variables to kafka
Using [apache single node docs](https://github.com/apache/kafka/blob/trunk/docker/examples/README.md#single-node) as a reference the only necessary step when using the default image in single mode is to set the replication factor to 1 (from 3). However when setting an environment variable it breaks the bootstrapping of configs so you have to add more environment variables. [See here for an example](https://github.com/apache/kafka/blob/trunk/docker/examples/jvm/single-node/plaintext/docker-compose.yml)
```yaml
services:
  kafka:
    image: apache/kafka
  environment:
      KAFKA_NODE_ID: 1
      KAFKA_ADVERTISED_LISTENERS: 'PLAINTEXT://kafka:9092'
      KAFKA_LISTENERS: 'CONTROLLER://:9093,PLAINTEXT://:9092'
      KAFKA_PROCESS_ROLES: 'broker,controller'
      KAFKA_CONTROLLER_QUORUM_VOTERS: '1@kafka:9093'
      KAFKA_INTER_BROKER_LISTENER_NAME: 'PLAINTEXT'
      KAFKA_CONTROLLER_LISTENER_NAMES: 'CONTROLLER'
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
      KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR: 1
```
The most important part is setting the advertised listener to kafka:9092 so that services inside docker can actually connect to it (it must be the same as the service name). The second most important part is setting this kafka service to a broker and controller so it can self manage itself.
> Instructor Aid: This is probably something they can figure out themselves after a bit of googling. However it is something they will have to do though, since they will have to overrided the `advertised listeners` since the default is localhost which will not work inside the docker containers.

## 3 - Make necessary changes to swarm.sh
1. Add stack variable
2. Remove sanity check + pass stack and compose file to deploy
3. Use stack destroy instead
4. Remove references to dev compose file

## 4 - Add kafka package to the project config.yaml file

# Hapi Proxy Setup

## 1 - Bootstrap Hapi Proxy package
Run the command `instant-linux package generate`
- Package name: hapi-proxy
- Name of package: Hapi Proxy training (not that important though)
- Docker image: jembi/springproxyserver:20211217-170809.3f57ef5
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no
> Instructor Aid: It's best to tell the trainees to go to the docker hub page itself to get the image tag. It can be found here: https://hub.docker.com/r/jembi/springproxyserver/tags

## 2 - Make necessary changes to swarm.sh
1. Add stack variable
2. Remove sanity check + pass stack and compose file to deploy
3. Use stack destroy instead
4. Remove references to dev compose file

## 3 - Add dependencies and environment variables to package-metadata.json
Since Hapi Proxy requires both hapi-fhir and kafka to function we need to add that to the dependency list, and while we are at it we can add the default environment variables.
```json
  "dependencies": ["kafka", "hapi-fhir"],
  "environmentVariables": {
    "HAPI_SERVER_URL": "http://hapi-fhir:8080/fhir",
    "KAFKA_HOSTS": "kafka:9092",
    "HAPI_SERVER_VALIDATE_FORMAT": "NONE"
  }
```
> Instructor Aid: You will have to give them the environment variable names since there is no documentation on the docker hub page nor on the github page (and the github repo is private anyway). Also be sure to remind them that the urls follow that of the service name they created. For example if we named our hapi-fhir service hapi-fhir-training the url would, by default, follow that convention and would instead be `http://hapi-fhir-training:8080`

## 4 - Update docker-compose.yml to add the environment variables
```yaml
services:
  hapi-proxy:
    image: jembi/springproxyserver:20211217-170809.3f57ef5
  environment:
    HAPI_SERVER_URL: ${HAPI_SERVER_URL}
    KAFKA_BOOTSTRAP_SERVERS: ${KAFKA_HOSTS}
    HAPI_SERVER_VALIDATE_FORMAT: ${HAPI_SERVER_VALIDATE_FORMAT}
```

## 5 - Add hapi-proxy entry to project config.yaml file

# Kafka Mapper Setup

## Bootstrap Kafka Mapper Consumer package
Run the command `instant-linux package generate`
- Package name: kafka-mapping-consumer
- Name of package: Kafka Mapping Consumer (not that important though)
- Docker image: jembi/eth-kafka-mapping-consumer:1.0.7
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no
> Instructor Aid: You'll ned to give them the image name and tag though since we don't tag latest to the latest version. So they will need to pass in the 1.0.7 version tag.

## 2 - Make necessary changes to swarm.sh
1. Add stack variable
2. Remove sanity check + pass stack and compose file to deploy
3. Use stack destroy instead
4. Remove references to dev compose file

## 3 - Add dependencies and environment variables to package-metadata.json
Since Hapi Proxy requires both hapi-fhir and kafka to function we need to add that to the dependency list, and while we are at it we can add the default environment variables.
```json
  "dependencies": ["kafka", "elastic-search"],
  "environmentVariables": {
    "ES_USERNAME": "elastic",
    "ES_PASSWORD": "dev_password_only",
    "ES_HOSTS": "elastic-search:9200",
    "KAFKA_HOSTS": "kafka:9092"
  }
```
You'll notice that we list elastic-search as a dependency to the array, this is intentional and necessary. The service won't start if it cannot connect to elastic search, however it does pose a problem as we do not have elastic search setup yet. This will be addressed through the use of a profile.
> Instructor Aid: You'll have to again give them these environment variables as the github page is a private repo and there is nothing on the docker hub page. Also just let them know that we will only be deploying + using this service once we do the elastic setup on the next day.

## 4 - Pass in these environment variables to the compose file
```yaml
  kafka-mapping-consumer:
    image: jembi/eth-kafka-mapping-consumer:1.0.7
    environment:
      ES_HOSTS: ${ES_HOSTS}
      ES_USERNAME: ${ES_USERNAME}
      ES_PASSWORD: ${ES_PASSWORD}
      KAFKA_HOSTS: ${KAFKA_HOSTS}
```

## 5 - Add kafka-mapping-consumer to the package list in the project file config.yaml

# Setup the profile
Since we now have quite a lot of services and even one that cannot be deployed yet, it is now time to introduce a profile. This will make it far easier to deploy all the services in one go but also customize it so we don't deploy services we cannot use / do not need.
```yaml
profiles:
  - name: training
    packages: 
      - reverse-proxy
      - openhim
      - hapi-fhir
      - kafka
      - hapi-proxy
    dev: true
    only: false
```

# Update networking
Since we have more services that need to be able to connect to each other we will need to define network definitions for them.

## 1 - Create the OpenHIM network
We will need to have OpenHIM to be able to route requests to hapi-proxy and so we need a network interface for it.
```yaml 
(openhim/docker-compose.yml)
  openhim-core:
    networks:
      reverse-proxy:
      public: # new part
      default:

networks:
  reverse-proxy:
    name: reverse-proxy_public
    external: true
  public: # new part
    name: openhim_public
    external: true
  default:
```

## 1.2 Attach hapi-proxy to OpenHIM network
```yaml
(hapi-proxy/docker-compose.yml)
services:
  hapi-proxy:
    networks:
      openhim:

networks:
  openhim:
    name: openhim_public
    external: true
```

## 2 - Create the kafka network
We will need to connect hapi-proxy and the mapper to the kafka network so they can consume/produce events.
```yaml
(kakfa/docker-compose.yml)
services:
  kafka:
    networks:
      public:

networks:
  public:
    name: kafka_public
    external: true
```

## 2.1 - Connect hapi proxy
```yaml
(hapi-proxy/docker-compose.yml)
services:
  hapi-proxy:
    networks:
      openhim:
      kafka: # new

networks:
  openhim:
    name: openhim_public
    external: true
  kafka: # new
    name: kafka_public
    external: true
```

## 2.2 - Connect Mapper
```yaml
(kafka-mapping-consumer)
services:
  kafka-mapping-consumer:
    networks:
      kafka:

networks:
  kafka:
    name: kafka_public
    external: true
```

# 3 - Create the hapi-fhir network
The final step is to create a hapi-fhir network since hapi-proxy will need to send requests to hapi-fhir.
```yaml
(hapi-fhir/docker-compose.yml)
services:
  hapi-fhir:
    networks:
      public:

networks:
  public:
    name: hapi-fhir_public
    external: true
```

# 3.1 - Attach hapi-proxy to hapi-fhir network
```yaml
(hapi-proxy/docker-compose.yml)
services:
  hapi-proxy:
    networks:
      openhim:
      kafka:
      hapi-fhir: # new

networks:
  openhim:
    name: openhim_public
    external: true
  kafka:
    name: kafka_public
    external: true
  hapi-fhir: # new
    name: hapi-fhir_public
    external: true
```

# Build + Setup Hapi Proxy Channel + Test
1. We can finally build and test. Build the image like normal `build-image.sh` but now we deploy using the profile `instant-linux package deploy --profile=training`
2. Navigate to localhost:80
3. Log in and navigate to channels
4. Create a new channel that routes requests matching the path /fhir.* to hapi-proxy:18080
> Instructor Aid: you will need to give them the port that hapi-proxy listens on 18080.
> Side note: You can check the channel setup on [QA](https://openhimconsole.qa.jembi.cloud/#!/channels) if you need help. Just make the channel public for simplicity.
5. Post a bundle to localhost:5001
6. Check OpenHIM transactions to see that it routed properly
7. Navigate to localhost:3447 and query the record you created to make sure it made it to hapi-fhir.

From this point onwards I'd advice against tearing down your setup since you'd have to readd the channel each time.
