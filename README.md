# docker-jolokia

Minimal Image with Apache Tomcat9, openjdk8-jre-base, [jolokia](https://jolokia.org/) and [hawtio](http://hawt.io/).


## jolokia

> Jolokia is remote JMX with JSON over HTTP.

> It is fast, simple, polyglot and has unique features. It's JMX on Capsaicin.

## hawtio

> hawtio has lots of plugins such as: a git-based Dashboard and Wiki, logs, health, JMX, OSGi,

> Apache ActiveMQ, Apache Camel, Apache OpenEJB, Apache Tomcat, Jetty, JBoss and Fuse Fabric

Since Version 1.4.0 needs `jolokia` an activated `Jsr160RequestDispatcher`.

This requires an activated authentication.
An `JOLOKIA_BASIC_AUTH` environment variable can be used to add users for a Basic Authentication:

For an example:
```bash
JOLOKIA_BASIC_AUTH="jolokia:passed,spec:test"
```


# Status

[![Docker Pulls](https://img.shields.io/docker/pulls/bodsch/docker-jolokia.svg)][hub]
[![Image Size](https://images.microbadger.com/badges/image/bodsch/docker-jolokia.svg)][microbadger]
[![Build Status](https://travis-ci.org/bodsch/docker-jolokia.svg)][travis]

[hub]: https://hub.docker.com/r/bodsch/docker-jolokia/
[microbadger]: https://microbadger.com/images/bodsch/docker-jolokia
[travis]: https://travis-ci.org/bodsch/docker-jolokia


# Build

Your can use the included Makefile.

To build the Container: `make build`

To remove the builded Docker Image: `make clean`

Starts the Container: `make run`

Starts the Container with Login Shell: `make shell`

Entering the Container: `make exec`

Stop (but **not kill**): `make stop`

History `make history`


# Docker Hub

You can find the Container also at  [DockerHub](https://hub.docker.com/r/bodsch/docker-jolokia/)


# Versions

- tomcat 9.0.16
- openjdk from alpine
- jolokia 1.6.0
- hawtio 2.5.0


# Tests

```bash
curl \
  http://localhost:8080/jolokia/ | jq
```

```bash
curl \
  http://localhost:8080/jolokia/list | jq
```

```bash
curl \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  http://localhost:8080/jolokia --data @examples/memory.json | jq
```

```bash
curl \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  http://localhost:8080/jolokia/read/java.lang:type=Memory/HeapMemoryUsage | jq
```


# Ports

- 8080
- 22222
