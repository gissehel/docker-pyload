PyLoad
=========

Introduction
----
pyLoad is a fast, lightweight and full featured download manager for many One-Click-Hoster, container formats like DLC, video sites or just plain http/ftp links. It aims for low hardware requirements and platform independence to be runnable on all kind of systems (desktop pc, netbook, NAS, router).

Despite its strict restriction it is packed full of features just like webinterface, captcha recognition, unrar and much more.

pyLoad is divided into core and clients, to make it easily remote accessible. Currently there are a webinterface, command line interface, and a GUI written in Qt.

Source [official pyload]

Install
----
Install is easy as all docker images

```sh
docker pull gissehel/pyload:latest
```

Running
----

```sh
docker run -d -P gissehel/pyload:latest
```

Configuration
----
You can link your Downloads to your host very easy like that:

```sh
docker run -d -v <host directoy>:/opt/pyload/Downloads -P gissehel/pyload:latest
```
Notice to replace ```<host directory>``` with your directory path on the host. So if you want to store your Downloads in ```/tmp/Downloads``` then your command would look like this:

```sh
docker run -d -v /tmp/Downloads:/opt/pyload/Downloads -P gissehel/pyload:latest
```
If you want to have your configuration persistent you have to link the configuration directory outside of the container. This can happen like this:

```sh
docker run -d -v <host directoy>:/opt/pyload/pyload-config -P gissehel/pyload:latest
```

By default, pyload will be run as root, and will download files with uid 0 and gid 0. If you want to change this behavior, you can specify the UID and GID that will be used for the downloaded files by using ENV VARS

```sh
docker \
    run \
    -d \
    -v <host download directory>:/opt/pyload/Downloads \
    -v <host config directoy>:/opt/pyload/pyload-config \
    -e UID=<uid> \
    -e GID=<gid> \
    -P \
    gissehel/pyload:latest
```

Finally
----
After the docker has created you can login via the webinterface with:

```sh
USER=pyload
PASSWORD=pyload
```

Links
-----

* official pyload page : http://pyload.org/
* Github page : https://github.com/gissehel/docker-pyload
* Docker hub page : https://hub.docker.com/r/gissehel/pyload
* Original github page : https://github.com/obi12341/docker-pyload
* Original docker hub page : https://hub.docker.com/r/gissehel/pyload

[official pyload]:http://pyload.org/

