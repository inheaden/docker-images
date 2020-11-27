# Inheaden docker images

This repository stores Dockerfiles and corresponding configurations for docker images used and maintained by [Inheaden](https://inheaden.io).

## Docker images

### maven-non-root

An image using JDK-11 and maven while running under a non-root user. This for example is required when running embedded databases (PostgresSQL) in docker containers.

### maven-go-docker

Specialized docker image for use with our internal CI system. Supplies maven, JDK-11, go and docker.

### go-docker

Specialized docker image to run integration tests of go applications using dockertest.

### jdk-11-non-root

Simple JDK 11 image running as non root.

## License

All images are licensed under the MIT-License.
