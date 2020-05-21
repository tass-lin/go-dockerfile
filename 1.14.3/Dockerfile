ARG GO_VERSION=1.14.3
ARG ALPINE_VERSION=3.11

FROM golang:${GO_VERSION}-alpine${ALPINE_VERSION}

RUN apk add --update supervisor \
    && rm -rf /var/cache/apk/*

COPY ./docker/supervisord.conf /etc/supervisor.d/supervisord.ini
    
CMD /usr/bin/supervisord -n -c /etc/supervisord.conf;