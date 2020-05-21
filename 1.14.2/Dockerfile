FROM golang:1.14.2-alpine3.11

WORKDIR /go/src/app

RUN apk add --update supervisor

COPY main.go .
COPY ./docker/supervisord.conf /etc/supervisor.d/supervisord.ini

RUN apk --update add  --virtual .build-deps git \
    && go get ./... \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/*
    
CMD /usr/bin/supervisord -n -c /etc/supervisord.conf;
