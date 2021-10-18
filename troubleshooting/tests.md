# Tests With Docker

This particular situation took me a lot to figure out how to deal with it, This section will be centered around how to include tests in a React App dockerized with jest

## **By Image**

Once we got some tests to run we can write an image including the test command

```docker
FROM node:14.17-alpine as builder

WORKDIR /app

COPY ["yarn.lock", "package.json", "./"]

RUN yarn install

COPY [".", "./"]

RUN yarn test && yarn dev
```

## **By Docker-compose**

We just need to raise up another services but this time overreding the command for the one to run our tests

```sh
version: "3.9"

services:
 # Other services stuff
 test:
    build:
      context: .
      dockerfile: development.Dockerfile
    environment:
      - CI=true
    command: yarn test
```

> Note: we set the environment variable "CI" to true because jest by default will run with --watch flag and will stay looking for changes

</br>

</br>

**See more: [Running react unit tests within docker Article](https://www.alanfoster.me/posts/running-react-unit-tests-within-docker/)**
