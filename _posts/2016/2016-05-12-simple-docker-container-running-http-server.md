---
layout: post
title:  "Simple Docker container running a http server"
date: 2016-05-12 09:00:00
tags: ['docker', 'container', 'static-website', 'http-server']
categories: docker container static-website http-server
---

In this exercise we will create a Docker container which will run a simple http server.

Before starting, setup Docker on your local machine. You can easily [setup Docker on your Windows machine using Chocolatey](/2016/05/11/settingup-docker-windows-chocolatey.html).


## Creating a Dockerfile   

We will create the Docker container using a ```Dockerfile```. A Dockerfile contains a set of instructions to tell docker how to create and configure the container.  

Create a directory with the name ```docker-playground```. 

Inside this directory, create a file name ```Dockerfile``` without extension.

Add the following line to the file.

```
FROM ubuntu:latest
```

This tells Docker that we want to create a new image using ```ubuntu:latest``` as the base image. Here ```ubuntu``` is the name of a repository and ```latest``` is a tag. This should be the first line in the file.

Optionally we can specify the name and email of the maintainer.

```
MAINTAINER Hemanshu Bhojak <hemanshubhojak@example.com>
```  

Now we will update ```apt-get``` and use it to install ```nodejs``` and ```npm```.

```
RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get install -y npm
```

```http-server``` is a simple, zero-configuration command-line http server. It serves files from the current directory over http. We can install it using ```npm```.

```
RUN npm install -g http-server
```

Create a symlink to the ```nodejs``` directory so that it can be run using the ```node``` command.

```
RUN ln -s /usr/bin/nodejs /usr/bin/node
```

Create a html file with some content in the ```docker-playground``` directory and name it index.html. We will add this file to the container.

```
ADD index.html /usr/apps/hello-docker/index.html
```    

Now we will set the working directory of the container to this path.

```
WORKDIR /usr/apps/hello-docker/
```

Lastly we will specify a command to run the http-server in silent mode by specifying the ```-s``` option.

```
CMD ["http-server", "-s"] 
```

Your Dockerfile should look like this.

```
FROM ubuntu:latest
MAINTAINER Hemanshu Bhojak <hemanshubhojak@example.com>

RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get install -y npm
RUN ln -s /usr/bin/nodejs /usr/bin/node

RUN npm install -g http-server

ADD index.html /usr/apps/hello-docker/index.html
WORKDIR /usr/apps/hello-docker/

CMD ["http-server", "-s"]
```

## Build the Dockerfile

Run the following command in your ```docker-playground``` directory.

```
docker build -t "playground:hello-docker" .
```

This command builds a container image in the ```playground``` repository and tags it ```hello-docker```.

To see the image you have just created, run the following command.

```
docker images
```

## Run the Docker Container

The following command will run the Docker container we just created.

```
docker run -pt 8080:8080 "playground:hello-docker"
```

The ```-t``` and ```"playground:hello-docker"``` specifies the container to run.

By default, ```http-server``` uses ```8080``` as the port. In order to access it on our host machine we need to expose it.

The option ```-p``` and ```8080:8080```  binds the host port to the container port. Here the first value is the container port and the other is the host port.

In order to test this we need to know the IP Address of the virtual machine which runs the container. 

Run the following command to find the IP Address of your Docker virtual machine. It is under the URL column and looks like ```tcp://<virtualmachine_ipaddress>:<port>```.

```
docker-machine ls
``` 

If everything went well you can see your ```index.html``` in the browser of your host machine using the following url.

```
http://<virtualmachine_ipaddress>:8080/index.html
```

## Some useful Docker commands

**List all Images**

```
docker images  
```

**List all Containers**

```
docker ps -a
```

**Delete an Image**

```
docker rmi <imageid>
```

**Delete a Container**

```
docker rm <containerid>
```
