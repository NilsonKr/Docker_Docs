# Docker Compose starter-pack

Docker has been doing good so far, but no great , since is tedious write all this large commands and instructions to raise up our containers and its even worst if we have more than one.

for this , docker-compose is the solution. we can write a config file in yml syntax to instruct how and what docker-compose should do it

# Basic explanation

The next file is used in the test project present in this directory

```yml
# It's the first line and indicate explicitly the version to use, the current version is '3.9' to date
version: '3.9'

# In this part we are going to set up all our container to run and their configurations

services:
  app:
  # Different containers from images to create
  db:
```

## Simplifying running containers

Instead of write too long commands we could write their configs here once and have them present any time

```yml
version: '3.9'

services:
  app:
    # Source image
    image: testapp
    # Enviroment variables needed
    environment:
      MONGO_URL: 'mongodb://db:27017/test'
    # Indicates that this container cannot run if the other service has failed, in this case our other cotnainer "db"
    depends_on:
      - db
    # Expose ports to our machine from container
    ports:
      - '3000:3000'

  db:
    # Soucer Image
    image: mongo
```

# Executing Docker-compose

Once we have our set up ready, we will just need to run in the directory

```sh
docker-compose up
```

this will throw a lot of logs but also will initialize our container and a dedicated network for them

```sh
# Initializing containers
project_db_1 is up-to-date
project_app_1 is up-to-date

# Creation of a network
Attaching to project_db_1, project_app_1

# Project Running
app_1  | Server listening on port 3000!
```

**Now We have running our project by a easier way using docker-compose ✨:)✨**
