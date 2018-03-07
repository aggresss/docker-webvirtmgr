
## Webvirtmgr Dockerfile

This repository contains **Dockerfile** of [Webvirtmgr](https://github.com/retspen/webvirtmgr).

### Installation

1. Install [Docker](https://www.docker.com/).

2. Pull the image from Docker Hub

```
$ docker pull aggresss/docker-webvirtmgr
```

### Usage

```
$ docker run -d -p 8080:8080 -p 6080:6080 aggresss/docker-webvirtmgr
```

It may takes 2 or 3 seconds for setting up Django database.

### Mount a Volume

You need to add a directory with its owner id "33".

```
mkdir /path/to/our/volume:/var/local/webvirtmgr
chown 33 /path/to/our/volume:/var/local/webvirtmgr
```

Then, you can mount this folder into your container.

``` 
$ docker run -d -p 8080:8080 -p 6080:6080 -v /path/to/our/volume:/var/local/webvirtmgr aggresss/docker-webvirtmgr
```
(deprecated)
Finally if you want the docker-webvirtmgr manage local virtual machine, please mount /var/run/libvirt/libvirt-sock to the container:

```
docker run -d \
--name webvirtmgr \
--privileged=true \
--restart=always \
-p 8080:8080 \
-p 6080:6080 \
-v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
webvirtmgr
```
and run this at host (deprecated) : chmod 777 /var/run/libvirt/libvirt-sork
