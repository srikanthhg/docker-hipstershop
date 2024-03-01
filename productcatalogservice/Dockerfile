FROM golang:1.21.3-alpine as builder
WORKDIR /src
COPY . .
RUN go build -o productcatalogservice

FROM alpine:3.18.4
WORKDIR /src
COPY --from=builder /src/productcatalogservice /src/productcatalogservice
COPY products.json .
EXPOSE 3550

ENTRYPOINT ["/src/productcatalogservice"]