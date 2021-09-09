# Data with Docker

The container is isolated from outside so it wont have access to outside data , and if we would like to preserve data of data base running in a container we could achieve this from different ways.

> Bind mounts

Bind a physic directory to a somewhere inside the container what we want to preserve

```sh
-v --volume <our_directory>:<container_directory>
```

```sh
docker run --name database -d -v COMPLETE_ROUTE/datadocker/mongodata:/data/db mongo
```

now we could work with the database and when we need to run another container we could load all our stuff with which we have bee working to the new container

**_CONS :_**

- the directory is public and accesible for anyone and for the container

> Volumes

Another way to handle the preservement of data is using volumes , the volumes are a space whichs is created by docker to store data, but with cannot access inside it , we just save data there.

### Creating a volume

</br>

```sh
docker volume ls

docker volume create my_data_volume

docker volume inspect my_data_volume
```

### Using a volume

</br>

```sh
 --mount src=<VOLUME>,dst=<CONTAINER_DIRECTORY>
```

```sh
docker run --name database -d --mount src=my_data_volume,dst=/data/db mongo
```

Now we have preservement of our data and security at the same time.

_**NOTE**_

> to get into the container once it is running

```sh
docker exec -it <CONTAINER_NAME|ID> bash
```
