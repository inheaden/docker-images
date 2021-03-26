FROM golang:1.16.2-alpine3.13

RUN adduser user --disabled-password

RUN chown -R user $(go env GOROOT)/pkg

RUN apk add docker
RUN apk add make
RUN apk add build-base

USER user

CMD [ "go" ]