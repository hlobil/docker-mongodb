docker-mongodb
==============

### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/recipediary/mongodb/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull recipediary/mongodb`

### Source
- [MongoDb Offical Build](https://registry.hub.docker.com/_/mongo/)

### Usage

#### Run `mongod`
``` bash
docker run -d \
  --name mongodb \
  --restart=always \
  -p 27017:27017 \
  recipediary/mongodb
```
#### Run `mongod` w/ persistent/shared directory
``` bash
docker run -d \
  --name mongodb \
  -p 27017:27017 \
  -v <db-dir>:/data/db \
  recipediary/mongodb
```
#### Run `mongod` w/ HTTP support
``` bash
docker run -d \
  --name mongodb \
  -p 27017:27017 \
  -p 28017:28017 \
  recipediary/mongodb mongod --rest --httpinterface
```
#### Run `mongod` w/ Smaller default file size
``` bash
docker run -d \
  --name mongodb \
  -p 27017:27017 \
  recipediary/mongodb mongod --smallfiles
```
#### Run `mongo` cli
``` bash
docker run -it --rm \
  --link mongodb:mongodb \
  recipediary/mongodb bash -c 'mongo --host mongodb'
```
