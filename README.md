# Graylog Docker Image

Latest stable version of Graylog is *2.5.1* this Version is available with the tags `2.5` or `2.5.1-4`.

## Folder Architecture
### Graylog
- /data/graylog
- /data/graylog/config
- /data/graylog/plugin

### MongoDB
- /data/mongo

### Elasticsearch
- /data/elasticsearch
`Folder permission should be uid:1000 / gid:1000`

## Installation
### Create folder graylog
- mkdir -p /data/graylog/config
- mkdir -p /data/graylog/plugin

### Get graylog configuration
- cd /data/graylog/config
- wget https://raw.githubusercontent.com/Graylog2/graylog-docker/2.5/config/graylog.conf
- wget https://raw.githubusercontent.com/Graylog2/graylog-docker/2.5/config/log4j2.xml

### Create folder mongodb
- mkdir -p /data/mongo

### Create folder elasticsearch
- mkdir -p /data/elasticsearch
- chown 1000:1000 -R /data/elasticsearch

### Start up
- pull graylog from this repository
- copy plugin to plugin folder /data/graylog/plugin
- docker-compose up -d

### Access to mongo shell
- docker exec -it [container id] bash
- mongo

### Drop mongodb via Mongo Shell
- mongo shell>use graylog
- db.dropdatabase()

### Dump data from mongodb
- docker exec -d [container_id] `mongodump -d graylog -o /yourpath/graylog-mongo`

### Restore MongoDB (Graylog Configuration)
- copy backup to server
- cd [path backup]
- docker exec -d [container id] `mongorestore -d graylog graylog/`

# Enjoy
