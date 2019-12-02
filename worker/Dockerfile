# FROM golang:1.6.2
FROM golang:1.12-alpine AS build-env

RUN apk add git --no-cache

WORKDIR /app

COPY go.mod .
COPY go.sum .

RUN go mod download
COPY . .

# RUN go get github.com/nats-io/nats
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -installsuffix cgo -o /go/bin/worker

# <- Second step to build minimal image
FROM scratch 
COPY --from=build-env /go/bin/worker /go/bin/worker
EXPOSE 8080
ENTRYPOINT ["/go/worker"]