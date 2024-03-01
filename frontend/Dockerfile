FROM golang:1.21.3-alpin as builder
WORKDIR /src
COPY . .
RUN go build -o myfrontend

FROM alpine:3.18.4
WORKDIR /src
COPY --from=builder /src/myfrontend /src/myfrontend
EXPOSE 8080
ENTRYPOINT ["/src/server"]