FROM golang:1.21.3-alpine as builder
WORKDIR /src
COPY . .
RUN go build -o myfrontend

FROM alpine:3.18.4
WORKDIR /src
COPY --from=builder /src/myfrontend /src/frontend
COPY ./templates ./templates
COPY ./static ./static
EXPOSE 8080
ENTRYPOINT ["/src/frontend"]