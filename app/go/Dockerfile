FROM golang:1.13.1-alpine3.10 AS based_builder

RUN apk add --no-cache git curl openssh
WORKDIR /src/go
COPY go.mod go.sum ./
RUN go mod download

FROM based_builder AS builder
WORKDIR /src/go
COPY . ./
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix nocgo -o /app .

FROM alpine:3.10
RUN apk update && \
   apk add curl ca-certificates && \
   rm -rf /var/cache/apk/** && \
   update-ca-certificates

COPY --from=builder /app ./
ENTRYPOINT ["./app"]
