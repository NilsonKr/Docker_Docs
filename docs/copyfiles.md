# Insert and Extract files

The way for handle files in case we are using volumes , is by the commando cp provided by docker

```sh
docker cp <FILE_PATH> <CONTAINER:PATH>

or

docker cp <CONTAINER:PATH> <NEW_FILE_PATH>
```

> Insert Files

```sh
docker cp filetest.txt mycontainer:/testdir/
```

> Extract files

```sh
docker cp mycontainer:/testdir/filetest.txt newfile.txt
```

_Now if you go to check the respective directories you will find each file we copy from our filesystem and inside the container_
