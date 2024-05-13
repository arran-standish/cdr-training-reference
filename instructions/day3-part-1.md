# Elasticsearch Setup

## 1 - Bootstrap Elasticsearch package
Run the command `instant-linux package generate`
- Package name: elasticsearch
- Name of package: Elasticsearch training (not that important though)
- Docker image: docker.elastic.co/elasticsearch/elasticsearch:7.13.0
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no
> Instructor Aid: They will need to use version 7 of Elastic, as that is the sdk version that the mapper consumer uses. So if you try and use the latest version (8.x) it will fail.

## 2 - Update the compose file to add required environment variables and volumes
The official Elasticsearch docs for setting up elastic search within docker is quite invovled as it sets up SSL as part of the process. As such we disable it through environment variables and set elastic to run in single mode.

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

## 1 - Bootstrap Kibana package
Run the command `instant-linux package generate`
- Package name: kibana
- Name of package: Kibana training (not that important though)
- Docker image: docker.elastic.co/kibana/kibana:7.13.0
- Description: what ever you want
- Stack: doesn't matter (cli still needs to be updated to correctly generate stack details)
- Type: doesn't matter
- Dev file: no
> Instructor Aid: They should match the versions of elastic and kibana

## 2 - Update the compose file to add required environment variables and networks
1. Set environment variables
```yaml
    environment:
      ELASTICSEARCH_HOSTS: ${ES_HOSTS} # pass in elastic url
      ELASTICSEARCH_PASSWORD: ${ES_ELASTIC} # elastic password
      ES_KIBANA_SYSTEM: ${ES_KIBANA_SYSTEM} # kibana password
```
2. Set elasticsearch network
```yaml
version: '3.9'

services:
  kibana:
    networks:
      elasticsearch:

networks:
  elasticsearch:
    name: elasticsearch_public
    external: true
```

## 3 - Make necessary changes to package-metadata.json
1. Add environment variable defaults
```json
  "environmentVariables": {
    "ES_HOSTS": "http:\/\/elasticsearch:9200",
    "ES_ELASTIC": "dev_password_only",
    "ES_KIBANA_SYSTEM": "dev_password_only"
  }
```
> Instructor Aid: Let them know that you will have to escape the /.

2. Add elasticsearch as a dependency
```json
  "dependencies": ["elasticsearch"],
```

## 4 - Make necessary changes to swarm.sh
1. Add stack variable
2. Remove sanity check + pass stack and compose file to deploy
3. Use stack destroy instead
4. Remove references to dev compose file

## 5 - Add kibana to the project config.yaml file and profile

## 6 - Nginx setup
Much like before we need to create a new server to listen on Kibana's port `5601` and expose that port on nginx side
1. Add the server to `reverse-proxy/config/nginx.conf`
```conf
  server {
    listen              5601;
    location / {
      resolver          127.0.0.11 valid=30s;
      proxy_pass        http://kibana:5601;
    }
  }
```
2. Add ports to `reverse-proxy/docker-compose.dev.yml`
```yaml
services:
  reverse-proxy:
    ports:
      # other ports above
      ...
      - target: 5601
        published: 5601
        mode: host
```
3. Attach kibana to reverse-proxy network
```yaml
services:
  kibana:
    networks:
      elasticsearch:
      reverse-proxy: # new

networks:
  elasticsearch:
    name: elasticsearch_public
    external: true
  reverse-proxy: # new
    name: reverse-proxy_public
    external: true
```

# Adding Kafdrop
Since online training was cut by a lot, it is unlikely that we will have covered the kafka cli and how to create topics using the cli. This is important since the kafka-mapping-consumer service will not start if the required topics are not present. To make it easier to create topics we add kafdrop as a service so we have a UI we can navigate to and can interact with to create topics and inspect topics etc.

## 1 - Add kafdrop to kafka compose file
```yaml
services:
  kafka:
    ...

  kafdrop:
    image: obsidiandynamics/kafdrop
    environment:
      KAFKA_BROKERCONNECT: "kafka:9092"
```
> Instructor aid: They will need to be given the topic list that they require up front. It is 2xx, patients, quarantine, and 4xx. 

## 2 - Attach kafdrop to the reverse-proxy network and kafka network
```yaml
services:
  kafdrop:
    networks:
      public: # needs to be able to communicate with kafka
      reverse-proxy:

networks:
  public:
    name: kafka_public
    external: true
  reverse-proxy: # new
    name: reverse-proxy_public
    external: true
```

## 3 - Add entry into nginx
By default Kafdrop listens on port 9000
```conf
  server {
    listen              9000;
    location / {
      resolver          127.0.0.11 valid=30s;
      proxy_pass        http://kafdrop:9000;
    }
  }
```

## 4 - Expose port 9000 on nginx
```yaml
services:
  reverse-proxy:
    ports:
      ...
      - target: 9000
        published: 9000
        mode: host
```

## 4 - Build the image + test changes
Run `build-image.sh` then `instant-linux package init --profile=training`
1. Check that you can access kibana on localhost:5601
2. Access kafdrop on localhost:9000 and create the topics: 2xx, 4xx, patients, quarantine
2. Setup OpenHIM channels (if you are coming from a clean slate)
3. Send some fhir data
4. Query the data in kibana to make sure data is entering elastic
