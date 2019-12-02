# FROM golang:1.6.2
FROM golang:1.12-alpine

COPY . /go

RUN apk add git --no-cache
# RUN go get github.com/nats-io/nats
# RUN go build worker.go

EXPOSE 8080
ENTRYPOINT ["/go/worker"]