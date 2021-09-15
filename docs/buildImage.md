# Building a Docker image

The way to build a docker image is by using a file called **Dockerfile** (it has to called exactly like that)

In that file we are going to write the instructions or template for run a container

> Basic Dockerfile

```docker
# Any Dockerfile always will start with the sentence FROM to indicate from what base image or software we are going to run build our image/layers

FROM ubuntu:latest

# The commands which we type here will occur in image build-time

RUN touch hello-Docker.txt
```

> Docker Build

In order to build our image and be able to run containers now we have run the build command

```sh
-t <TAG_NAME> e.g <REPOSITORY>/<BASE_IMAGE>:<CUSTOM_TAG>

docker build -t nilsonkr/ubuntu:mytag . # <-- Access directory

```

this is how docker build our layers as a Image

![Docker Layers](https://static.platzi.com/media/user_upload/Screenshot%20from%202020-11-06%2019-53-30-a305c998-0991-44ad-9319-80cacb1a4bc7.jpg)

> Running container

_**Remember** if we run a container without a tag , docker will look for "latest" tag_

```sh
docker run -it nilsonkr/ubuntu:mytag


# Result
root@eb69901907be:/# ls
#          Here is our file!
#                  ↓
bin   dev  hello-docker.txt  lib    lib64   media  opt   root  sbin  sys  usr
boot  etc  home

```

## Publish a image

for upload a image to our repository in Docker hub we need first to do login

```sh
docker login

Authenticating with existing credentials...
Login Succeeded
```

and then we could push our image

```sh
docker push nilsonkr/ubuntu:mytag
```

</br>

> > **Plus** Retag a image

```
docker tag <ID or IMAGE_NAME> repository/ubuntu:newtag
```

### When we retag a image, there are 2 images , the old one and new one, actually docker doesn't create a new Image , docker only create a new tag what is pointing to the last layer of our already created image.

</br>

![Docker retag](https://i.ibb.co/JBL946b/Screenshot-at-Feb-05-15-26-18.png)

### **then if you want you could remove the old one**
