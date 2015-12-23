FROM kallikrein/node:4.2.3

MAINTAINER Thomas Charlat "thomas.charlat@gmail.com"

RUN npm i -g http-master

VOLUME /logs
VOLUME /certificates
VOLUME /static
VOLUME /conf

ENTRYPOINT http-master --config /conf/http-master.conf
