FROM golang:latest as builder

WORKDIR /app

COPY . .

RUN go get
RUN CGO_ENABLED=0 GOOS=linux go build  -o consignment-service -a -installsuffix cgo main.go

FROM alpine:latest

RUN apk --no-cache add ca-certificates

RUN mkdir /app
WORKDIR /app
COPY --from=builder /app/consignment-service .

CMD ["./consignment-service"]
