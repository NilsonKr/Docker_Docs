# Development Apps with Docker

For this example we are going to use a tiny and simple node.js app inside the directory named "project"

this app already has a _DockerFile_ and other weir things, for now we will analyze what does this **DockerFile**

```docker
# Start from nodejs image in its 12 tag/version
FROM node:12

# We will to copy our whole project to a directory inside the container
COPY [".", "/usr/src/"]

# We are going to move to that directory and start working
WORKDIR /usr/src

# Install all node dependencies usibn npm
RUN npm install

# Expos the port which our app will run
EXPOSE 3000

# Deafult Command to run ur app
CMD ["node","index.js"]

```

We only has set up all that we need to run our app

```sh
docker build -t testapp .

# Run container
docker run --rm -d -p 3000:3000 testapp
```

**But** we have a couple of problems

> FIRST: We will need to re-install everything if we made some change

> SECOND: We will need to build again if we made some change

# Using Docker Cache

if we made any change inside our project files in our current structure we will need to re-install everything and docker wont be able to re-use stuff from it's cache

The solution is pretty simple, analyzing our `DockerFile` we can realize that we needn't move our whole project first and then install dependencies we could only move the necessary files and then the rest of our project , so let's do it!

```docker
FROM node:12

# We just move the necessary files to install dependencies first
COPY ["package.json", "package-lock.json", "/usr/src/"]

WORKDIR /usr/src

# Install dependencies with the necessary files already in the directory
RUN npm install

# Now we can move the res of our project and this will free us to install dependencies again
COPY [".", "/usr/src"]

EXPOSE 3000

CMD ["node","index.js"]
```

**Note**: _At the second copy we are moving 'package.json' and 'package-lock.json' again but docker is smart enough to realize that this files already exists and there are no changes so docker will just ignore them_

# Listening for Changes

now the next issue that we need to solve , is to be able to develop and at the same time see the changes reflected in our app running at docker container

> _This could be solved with other docker tool but for now we are going to implement other strategy ;)_

We can bind our develop directory to directory inside docker container with bind-mounts

```sh
docker run --rm -d -p 3000:3000 -v $(pwd)/index.js:/usr/src/index.js testapp

```

**Note**: We just bind our files directory or file because if we bind our whole directory project we will hide or override the directory inside the container so we will have not dependencies and anything installed
