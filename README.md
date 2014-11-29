docker-mongodb
==============

### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/hlobil/mongodb/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull hlobil/mongodb`


### Usage

#### Run `mongod`
``` bash
docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb
```
#### Run `mongod` w/ persistent/shared directory
``` bash
docker run -d \
    -p 27017:27017 \
    -v <db-dir>:/data/db \
    --name mongodb \
    hlobil/mongodb
```
#### Run `mongod` w/ HTTP support
``` bash
docker run -d \
    -p 27017:27017 \
    -p 28017:28017 \
    --name mongodb \
    hlobil/mongodb mongod --rest --httpinterface
```
#### Run `mongod` w/ Smaller default file size
``` bash
docker run -d \
    -p 27017:27017 \
    --name mongodb \
    hlobil/mongodb mongod --smallfiles
```
#### Run `mongo` cli
``` bash
docker run -it --rm \
    --link mongodb:mongodb \
    hlobil/mongodb bash -c 'mongo --host mongodb'
```
