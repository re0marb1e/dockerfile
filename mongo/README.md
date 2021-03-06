# Mongo Dockerfile

This Dockfile is used to run the Mongo server.

## Build the image

You can pull this docker image from [mongo](https://hub.docker.com/_/mongo/).

```shell
docker pull mongo:4.0.4
```

## Run the container

```shell
export DOCKER_MONGO_VERSION=4.0.4;
docker volume create mongo-data;
docker run --rm -v mongo-data:/volume -v $(pwd):/mongo-conf mongo:$DOCKER_MONGO_VERSION bash -c 'mkdir -p /volume/conf /volume/db /volume/mount && cp /mongo-conf/mongod.conf /volume/conf/mongod.conf && chown mongodb /volume/db';
docker run -d -p 27017:27017 -v mongo-data:/volume --name mongo mongo:$DOCKER_MONGO_VERSION --config /volume/conf/mongod.conf;
```

## Auth

Enter into mongo shell

```shell
docker exec -it mongo mongo
```

Execute following in mongo shell

```
use admin;
db.createUser(
  {
    user: "admin",
    pwd: "7eunEXjwxu",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
  }
);
db.createUser(
  {
    user: "userAdmin",
    pwd: "MTbDjZB9AV",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
);
exit;
```

To enable auth in mongo:

-   You can delete original docker contianer and run the following one
    
    ```
    docker rm -f mongo
    docker run -d -p 27017:27017 -v mongo-data:/volume --name mongo mongo:$DOCKER_MONGO_VERSION --config /volume/conf/mongod.conf --auth;
    ```

-   Or add "security.authorization: enabled" to the the mongod.conf file

## Import sample data

The sample data is provided by [ozlerhakan/mongodb-json-files](https://github.com/ozlerhakan/mongodb-json-files)

Enter into mongo shell

```shell
docker exec -it mongo mongo
```

Execute following in mongo shell

```
use admin;
db.auth('admin', '7eunEXjwxu');
use alpha;
db.createUser(
  {
    user: "alphaOwner",
    pwd: "JDgwiiRw6w",
    roles: [ { role: "dbOwner", db: "alpha" }]
  }
);
db.createCollection('students');
exit;
```

Import data

```
cp ./datasets/* /data/mongo/mount/
docker exec -it mongo mongoimport -u alphaOwner -p JDgwiiRw6w -d alpha -c students /mount/students.json
```