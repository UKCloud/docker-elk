# ELK-Stack on Openshift v3

**Under construction**

These are modified dockerfiles from the official docker images. I removed the gosu stuff and made sure relevant files are world readable.

## Usage
There is a docker-compose and a openshift template file in the `example` directory.
### Local
```

cd s2i
docker-compose run s2i s2i build https://github.com/UKCloud/docker-elk.git lbischof/logstash logstash --context-dir=example
cd ..
docker run -it --rm --name elasticsearch lbischof/elasticsearch
docker run -it --rm --link elasticsearch:elasticsearch -p 5601:5601 lbischof/kibana

docker run -it --rm --link elasticsearch:elasticsearch logstash
```

