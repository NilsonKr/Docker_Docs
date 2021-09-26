# Docker Network's

In order to comunicate containers among them , we have to put them inside a docker network,
a Docker network it's like a lan network dedicated for containers and provides a way to comunicate among

# Network commands

### _List docker networks_

```sh
docker network ls

NETWORK ID     NAME      DRIVER    SCOPE
e59f121f849d   bridge    bridge    local
976dc1e5127f   host      host      local
003c9b4a32df   none      null      local
```

### _Create Network_

```sh
docker network create myNetwork
```

you can also create allowing standalone container connections

```
docker network create --attachable myNetwork
```

# Connecting Containers

to connect containers into networks you just have to indicate which one will connect to

```sh
docker run --myContainer --newtork myNetwork <IMAGE>
```

or if it's a container that is already running and you newtork allow standalone connections you could connect it by this:

```sh
docker network connect <NETWORK_NAME> <CONTAINER_NAME|ID>
```

</br>

</br>

</br>

> **There are other many configurations and feature about networking in docker, you could fine some more here**

`https://docs.docker.com/network/`
