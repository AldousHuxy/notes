# Docker
> "It works on my computer" - Literally everyone
 - [Docker](https://www.docker.com/) is a platform for building, running and shipping applications.
 - The Docker platform is a Linux-based platform that allows developers to create and execute containers, self-contained programs, and systems that are independent of the underlying infrastructure.
 - Docker, which is based on the Linux kernel’s resource isolation capabilities, allows developers and system administrators to transfer programs across multiple systems and machines by executing them within containers.

## Virtual Machines vs. Containers
 - A virtual machine is an abstraction of a machine (physical hardware).
 - A container is an isolated environment for running an application.

![Containers v. VM's](https://assets-global.website-files.com/60494527fea68422687bfcf1/60620c306c8eb076474a5b90_virtual-machines-vs-containers-1024x582.png)

## Hypervisors
- VirtualBox
- VMware
- Hyper-v (windows)

## Docker Images
 - Allow running multiple applications in isolation
 - Lightweight
 - Use OS of the host
 - Starts quickly
 - Needs less hardware resources

## Docker Files
- A `Dockerfile` is a script that uses the Docker platform to generate containers automatically.

## Example
 - Even a simple console log in JavaScript requires a lot of resources for another machine to run!
 - Your application is contingent on a number of instructions in order to run.
```js
// File: my-app/app.js
console.log('My App!')
```
### Instructions
 - Start with an OS
 - Install Node
 - Copy app files
 - Run node app.js

### Dockerfile
```docker
FROM node:alpine
COPY ./app
WORKDIR /app
CMD node app.js
```

```bash
$ docker build -t my-app .
```

## View Docker Images
```bash
$ docker image ls
REPOSITORY  TAG     IMAGE ID    CREATED         SIZE
my-app      latest  234587909   2 minutes ago   112MB
```

# Docker Compose