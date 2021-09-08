# Expose container at a local port

When we are trying to run a service which listen in a port within a Docker container , the service will listen at a port in the container, not in our machine

```sh
docker run --name proxy -d nginx
```

```sh
docker ps

CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
539826e0e645   nginx     "/docker-entrypoint.…"   3 seconds ago   Up 2 seconds   80/tcp    proxy
```

in order to bind or expose the port in the container with the outside, we could set up the ports:

```sh
-p --publish <port_at_local_machine:port_at_container> # Set ports
```

```sh
docker run --name proxy -d -p 8080:80 nginx

docker ps

PORTS
0.0.0.0:8080->80/tcp, :::8080->80/tcp # now its exposed
```

so we can go and check it in the browser at http://localhost:8080

## Check Logs

> with the container running in background we can't see the stdout but we could check the logs by the following way

```
docker logs proxy


2021/09/08 03:55:12 [notice] 1#1: start worker process 38
2021/09/08 03:55:12 [notice] 1#1: start worker process 39
2021/09/08 03:55:12 [notice] 1#1: start worker process 40
2021/09/08 03:55:12 [notice] 1#1: start worker process 41
2021/09/08 03:55:12 [notice] 1#1: start worker process 42
```

> to see it updated

```
docker logs < -f | --follow > proxy


2021/09/08 03:55:12 [notice] 1#1: start worker process 38
2021/09/08 03:55:12 [notice] 1#1: start worker process 39
2021/09/08 03:55:12 [notice] 1#1: start worker process 40
2021/09/08 03:55:12 [notice] 1#1: start worker process 41
2021/09/08 03:55:12 [notice] 1#1: start worker process 42
```
