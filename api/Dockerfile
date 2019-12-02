# FROM golang:1.6.2
FROM golang:1.12-alpine

RUN apk add git --no-cache

WORKDIR /app

COPY ./go.mod .
COPY ./go.sum .


RUN go mod download
COPY . .

# RUN go get github.com/nats-io/nats
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -installsuffix cgo -o api-server.go

# <- Second step to build minimal image
FROM scratch 
# COPY --from=build-env /go/bin/hello /go/bin/hello
EXPOSE 8080
ENTRYPOINT ["/app/api-server"]


