FROM ubuntu:bionic

RUN apt-get -yq update \
  && apt-get -yq install software-properties-common curl ca-certificates \
  && add-apt-repository ppa:longsleep/golang-backports \
  && apt-get -yq update \
  && apt-get -yq install openjdk-11-jdk curl golang-go git \
  && rm -rf /var/lib/apt/lists/*

RUN adduser maven --disabled-password

ENV DOCKER_CHANNEL stable
ENV DOCKER_VERSION 19.03.8
RUN curl -fsSL "https://download.docker.com/linux/static/${DOCKER_CHANNEL}/x86_64/docker-${DOCKER_VERSION}.tgz" \
  | tar -xzC /usr/local/bin --strip=1 docker/docker

ARG MAVEN_VERSION=3.6.3
ARG USER_HOME_DIR="/home/maven"
ARG SHA=c35a1803a6e70a126e80b2b3ae33eed961f83ed74d18fcd16909b2d44d7dada3203f1ffe726c17ef8dcca2dcaa9fca676987befeadc9b9f759967a8cb77181c0
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/${MAVEN_VERSION}/binaries

RUN mkdir -p /usr/share/maven /usr/share/maven/ref \
  && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
  && echo "${SHA}  /tmp/apache-maven.tar.gz" | sha512sum -c - \
  && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1 \
  && rm -f /tmp/apache-maven.tar.gz \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn

ENV MAVEN_HOME /usr/share/maven
ENV MAVEN_CONFIG "$USER_HOME_DIR/.m2"

COPY settings.xml $MAVEN_CONFIG/settings.xml
RUN mkdir $MAVEN_CONFIG/repository
RUN chown maven:maven $USER_HOME_DIR -R

USER maven

CMD [ "mvn" ]