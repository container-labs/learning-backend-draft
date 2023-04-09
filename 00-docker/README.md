# Docker

Docker, or more appropriately "OCI Containers" is a way to package software and run software in a predictable and reliable way with a consistent interface. 


Not all containers are Docker containers. When people say Docker, they most likely mean OCI Containers, which is a standard established by the [Open Container Initiative](https://opencontainers.org/). 


### Install "Docker"

The fastest way to get started is with [Docker Desktop](https://docs.docker.com/desktop/), a product from the company Docker.

If you're looking for the more modern way to work with OCI Containers, I'd reccomend installing [Colima](https://github.com/abiosoft/colima).

### Your First Dockerfile

```docker
FROM ubunut:latest

RUN echo "hello world"
```

Using `latest` is an anti-pattern that deserves an entire blog to explain. It mostly deals with you not knowing what version is _actually_ deployed. Also, when a k8s cluster scales up, `latest` can mean different things and you'll have mixed, non-declarative state. 

To build this Dockerfile, simply run `docker build .`. 

### Your Second Dockerfile

```docker
FROM node:latest

RUN node -v
```

### Adding Things To A Dockerfile

```docker
FROM node:latest

COPY package.json package.json
RUN yarn install
COPY . .

CMD ["yarn", "start"]
```
