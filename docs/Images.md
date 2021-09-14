# What is a Docker image ?

We have been working with public images from docker hub, which allow us to run a variety of projects, so we can say a Image is the base compress version of a project.

A Image is what Classes are for instances in OOP, and container will be those instaces of a image,

_A image can be formed by several layers until get the expected result_

_graphic e.g_

![Docker Image](https://static.packt-cdn.com/products/9781788992329/graphics/0ee3d4cf-2133-4143-a7c4-690274483841.png)

In summary a docker image is a file which we can run code in a docker container , like a template to set up our container running our application instructed by the image file, a Docker image contains application code, libraries, tools, dependencies and other files needed to make an application run.

> See images

```sh
docker image ls

REPOSITORY          TAG       IMAGE ID       CREATED        SIZE
docker101tutorial   latest    4459ef157996   8 days ago     28.2MB
nginx               latest    822b7ec2aaf2   10 days ago    133MB
mongo               latest    0bcbeb494bed   2 weeks ago    684MB
ubuntu              latest    fb52e22af1b0   2 weeks ago    72.8MB
alpine/git          latest    b8f176fa3f0d   3 months ago   25.1MB
hello-world         latest    d1165f221234   6 months ago   13.3kB
```

**Note the tags are like images version if you dont specify anyone docker will pull the latest**

</br>

> Retrieve images from Docker hub

```sh
docker pull <IMAGE_NAME>

docker pull ubuntu:20.04

```

## _More about images [here](https://searchitoperations.techtarget.com/definition/Docker-image)_
