<a name="top"></a>
# Docker Information

This section details how you can find out information about your docker installation.

The container running.

The images etc.

All references are taken from the docker website: 

> Get Started, Part 1: Orientation and setup

[https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)

## Topics

* [docker --version](#docker-version)
* [docker version](#docker-version--)
* [docker info](#docker-info)
* [docker run hello-world](#docker-helloworld)
* [docker run -it ubuntu bash](#docker-run)
* [docker image ls](#docker-image-ls)
* [docker container ls](#docker-container-ls)
* [docker container ls --all](#docker-container-ls--all)
* [Recap and cheat shee](#recap)

<a name="docker-version"></a>

### docker --version

```bash
$ docker --version
Docker version 17.05.0-ce, build 89658be
```
[top](#top)

<a name="docker-version--"></a>

### docker version  (without --)

When you run `docker --version` without `--` then you receive more information about docker itself.

```bash
$ docker version

Client:
 Version:      17.05.0-ce
 API version:  1.29
 Go version:   go1.7.5
 Git commit:   89658be
 Built:        Thu May  4 22:10:54 2017
 OS/Arch:      linux/amd64

Server:
 Version:      17.05.0-ce
 API version:  1.29 (minimum version 1.12)
 Go version:   go1.7.5
 Git commit:   89658be
 Built:        Thu May  4 22:10:54 2017
 OS/Arch:      linux/amd64
 Experimental: false

```

[top](#top)

<a name="docker-info"></a>

## $ sudo docker info | head -n 6

```bash
$ sudo docker info | head -n 6

Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 14
Server Version: 17.05.0-ce

```

[top](#top)

<a name="docker-helloworld"></a>

### $ docker run hello-world

To test that the docker machine is running correctly. Run the following command.

This will download the hello world test project from docker itself.


```bash
$ sudo docker run hello-world

Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete
Digest: sha256:66ef312bbac49c39a89aa9bcc3cb4f3c9e7de3788c944158df3ee0176d32b751
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/

```

[top](#top)

<a name="docker-run"></a>

### docker run -it ubuntu bash

The last example said for us to try this next command out `$ docker run -it ubuntu bash` to see what happens.

> Prior to writing this README.md and project I had run this command many time, therefore it will output a different result to yours.

```bash
$ docker run -it ubuntu bash

Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
1be7f2b886e8: Already exists 
6fbc4a21b806: Already exists 
c71a6f8e1378: Already exists 
4be3072e5a37: Already exists 
06c6d2f59700: Already exists 
Digest: sha256:e27e9d7f7f28d67aa9e2d7540bdc2b33254b452ee8e60f388875e5b7d9b2b696
Status: Downloaded newer image for ubuntu:latest


```

This then moves your bash terminal into the `ubuntu` image.

```bash
root@d336e275ed8b:/#

cat /etc/*-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
NAME="Ubuntu"
VERSION="16.04.3 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.3 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial

```

[top](#top)

<a name="docker-image-ls"></a>

### $ docker image ls

> Lists all images downloaded to your machine

```bash
$ sudo docker image ls

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              latest              0458a4468cbc        2 weeks ago         112MB
hello-world         latest              f2a91732366c        2 months ago        1.85kB
```

[top](#top)

<a name="docker-container-ls"></a>

### $ docker container ls

Since we have run the following 2 commands:

```bash
$ docker run hello-world
$ docker run -it ubuntu bash
```

This means that docker has created a container for each of the images every time that they have been run.

If we run `docker container ls` now we set that it does not list any containers

```bash
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```
[top](#top)

<a name="docker-container-ls--all"></a>

### $ docker container ls --all

Both images which were run & exitted.

Only running containers are listed with `docker container ls`.

To see all containers the `--all` option is required

```bash
$ sudo docker container ls --all

CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
533cf913a1c2        ubuntu              "bash"              5 seconds ago       Exited (0) 1 second ago                        vigilant_archimedes
3378064dc437        hello-world         "/hello"            4 minutes ago       Exited (0) 4 minutes ago                       xenodochial_payne
``` 

[top](#top)

<a name="recap"></a>

## Recap and cheat sheet

> List Docker CLI commands

```bash
docker
docker container --help
```
> Display Docker version and info

```bash
docker --version
docker version
docker info
```
> Excecute Docker image

```bash
docker run hello-world
```
> List Docker images

```bash
docker image ls
```
> List Docker containers (running, all, all in quiet mode)

```bash
docker container ls
docker container ls -all
docker container ls -a -q
```
[top](#top)