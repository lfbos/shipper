FROM golang:alpine

RUN apk --no-cache add git ca-certificates

WORKDIR /go/src/github.com/lfbos/shipper/vessel-service

COPY . .

RUN go get -u github.com/golang/dep/cmd/dep
RUN dep init && dep ensure
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo .

CMD ["./vessel-service"]
