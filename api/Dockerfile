# FROM golang:1.6.2
FROM golang:1.12-alpine

RUN apk add git --no-cache

WORKDIR /app

#
COPY . .

# 
RUN go mod download

# RUN go get github.com/nats-io/nats
RUN go build api-server.go

EXPOSE 8080
ENTRYPOINT ["/go/api-server"]