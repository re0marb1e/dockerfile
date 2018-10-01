# Drakov Dockerfile

This Dockfile is used to mock server that implements the API Blueprint specification.

## Build the image

```Dockerfile
cd /path/to/dockerfile
docker build -t re0marb1e/drakov:1.0.0 .
```

Or you can also pull this docker from [re0marb1e/drakov](https://hub.docker.com/r/re0marb1e/drakov/)

```Dockerfile
docker pull re0marb1e/drakov:1.0.0
```

## Run the container

```Dockerfile
cd /path/to/drakov/repository
export DOCKER_DRAKOV_VERSION=1.0.0
docker run -p 3000 -d --name drakov -v $PWD:/blueprints re0marb1e/drakov:$DOCKER_DRAKOV_VERSION
```