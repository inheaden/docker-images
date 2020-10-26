FROM golang:1.15.3-alpine3.12

RUN adduser user --disabled-password

RUN apk add docker

USER user

CMD [ "go" ]