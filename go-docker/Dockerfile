FROM golang:1.15.3-alpine3.12

RUN adduser user --disabled-password

RUN apk add docker
RUN apk add make

USER user

CMD [ "go" ]