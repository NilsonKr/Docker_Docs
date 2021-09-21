# Development with Docker-compose

With docker-compose we have a tool which allow us to automate all those tedious commands that we used to write in the bash

but we still need to do some changes and configurations to achive a equal behavior

## Building images with Docker compose

> we can build a image as part of one service

```docker-compose
version: '3.9'

services:
  app:
    # Here we will build the current dir in a image
    build: .
    environment:
      MONGO_URL: 'mongodb://db:27017/test'
    depends_on:
      - db
    ports:
      - '3000:3000'
  db:
    image: mongo

```

to execute only the build of our services who have a build process inside

```sh
docker-compose build
```

## Automating the bind-mounts with docker-compose

as we saw before , we need to bind the files that we are editing to the content inside the container, this could be solved really easy with volumes inside services

```docker-compose
version: '3.9'

services:
  app:
    # Here we are going to declare our volume to use at first line, in the lines below we set which files docker should ignore in order to dont override the content inside the container e.g node_modules when we bind
    volumes:
      - .:/usr/src
      - /usr/src/node_modules
  db:
    image: mongo

```

## Overriding default command

to finish we are missing one step more , and it's monitoring our files to reflect the changes in our app

but our image built from "Dockerfile" has as default command run "node index.js" and clearly this won't refresh our changes
despite we have binded our files

> we can override the default command of a container with docker-compose file

```docker-compose
version: '3.9'

services:
  app:
    # with command we say what command should execute when the container runs overriding its default one
    command: npx nodemon index.js
  db:
    image: mongo

```

</br>

</br>

</br>

> **NOTE:** It's very common to find an abbreviation for 'docker-compose' command which is 'fig' due to it was the original name of docker-compose project before docker decided to officially acquire it

_We can set up as an alias_

```sh
alias fig="docker-compose"

docker-compose up

🚀🚀🚀🚀🌟🌟✨🌟🌟🚀🚀🚀🚀
```
