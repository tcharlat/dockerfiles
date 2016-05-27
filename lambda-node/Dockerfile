FROM kallikrein/ubuntu:14.04
MAINTAINER Thomas Charlat "thomas.charlat@gmail.com"

RUN curl https://nodejs.org/dist/v4.3.2/node-v4.3.2-linux-x64.tar.xz | tar xz -C /usr/local/ --strip=1
RUN \
  apt-get update && \
  apt-get install -y imagemagick
VOLUME /src
WORKDIR /src
