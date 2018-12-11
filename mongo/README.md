# Mongo Dockerfile

This Dockfile is used to run the Mongo server.

## Build the image

You can pull this docker image from [mongo](https://hub.docker.com/_/mongo/).

```shell
docker pull mongo:4.0.4
```

## Run the container

```shell
mkdir -p /data/mongo/conf /data/mongo/db
cp ./mongod.conf /data/mongo/conf/mongod.conf
export DOCKER_MONGO_VERSION=4.0.4
docker run -d -p 27017:27017 -v /data/mongodb/conf:/etc/mongo -v /data/mongodb/data:/data/db --name mongo -d mongo:$DOCKER_MONGO_VERSION --config /etc/mongo/mongod.conf
```