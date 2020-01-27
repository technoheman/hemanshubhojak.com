---
layout: post
title:  "Setting up Docker on Windows using Chocolatey"
date: 2016-05-11 08:31:00
tags: ['docker', 'windows', 'chocolatey', 'container']
categories: docker windows chocolatey container
---

## Installing Chocolatey

[Chocolatey](https://chocolatey.org/) is an [awesome package manager for Windows](/2016/05/11/chocolatey-a-package-manager-for-windows.html) (like apt-get) which makes installing software a breeze.

Run the following command to download and install Chocolatey.

```
C:\>  @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

Verify that we have successfully installed Chocolatey.

```
C:\> choco -v
```

## Installing Docker Components

We will need the following components in order to create and host [Docker](https://www.docker.com/) containers on our local machine.

 1. VirtualBox
 2. Docker Client
 3. Docker Machine
 4. Docker Compose
 
### Virtual Box

Docker uses virtual machines to host and run containers. It supports VirtualBox, VMWare, Hyper-V along with some other cloud based virtualization products.

For this exercise we will use VirtualBox. Run the following command to install VirtualBox.

```
C:\> choco install virtualbox
```

### Docker Client

Docker client is used to manage images and containers. It is used to build images and run containers.

```
C:\> choco install docker
```

Verify

```
C:\> docker -v
Docker version 1.11.1, build 5604cbe
```

### Docker Machine

Containers are run within virtual machines. Docker machine is used to create and manage virtual machines.

```
C:\> choco install docker-machine
``` 

Verify

```
C:\> docker-machine -v
docker-machine version 0.7.0, build a650a40
```

### Docker Compose

Docker compose is mainly used to compose and run multiple docker containers. This is useful when we have separate containers to run the application, database, etc. 

```
C:\> choco install docker-compose
```

Verify

```
C:\> docker-compose -v 
docker-compose version 1.7.1, build unknown
```

## Finally, our first docker container :)

Now that we have all the required components in place, let us create and run our first container.

Use the following command to create a docker virtual machine with the name ```mydockervm```.

```
C:\> docker-machine create -d virtualbox mydockervm
``` 

It will take a while for the virtual machine to be ready. After this command completes, run the following to check the status of the virtual machine.

```
C:\> docker-machine ls
NAME         ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
mydockervm   *        virtualbox   Running   tcp://192.168.99.100:2376           v1.11.1   
```

We can have multiple docker virtual machines running on the same physical machine. 

Before we can create our container, we will have to setup some environment variables to tell docker client about our virtual machine.

Docker supports ```bash```, ```cmd```, ```powershell``` and ```emacs``` at the time of writing this post. Since we are on Windows we will use ```powershell```.

```
C:\> docker-machine env --shell powershell mydockervm | iex
```
 
Finally let us create and run our first docker container.

```
C:\> docker run --rm -it ubuntu bash
```

You should see a bash prompt once the container has started. Type ```exit``` to stop the container.

The ```--rm``` options tells docker to delete the file system after the container stops.

```-it``` along with ```bash``` in layman terms runs the container in interactive mode where we can use the container's bash.  
