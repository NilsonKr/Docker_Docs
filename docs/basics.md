# Docker getting started commands

> Run container

```
docker run <container_name>
```

> List containers

```sh
docker ps   #current running

docker ps -a/--all  #stopped too
```

> Inspect low-level container especs

```sh
docker run <container_name> or <container_id>
```

> Delete containers

```sh
docker rm <container_name> or <container_id>

docker container prune #delete all stopped containers
```

</br >

## _Other utilities_

</br >

> Naming containers

```sh
docker run --name <name_assigned> <container_name>

#e.g docker run --name custom_hello hello-world

docker rename <container_name> <new_name>

```
