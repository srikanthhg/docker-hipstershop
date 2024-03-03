FROM golang:1.21.3-alpine as builder

WORKDIR /app

COPY . .

RUN go build -o checkoutservice

########################
FROM alpine:3.18.4

WORKDIR /app

COPY --from=builder /app/checkoutservice /app/checkoutservice

Env PRODUCT_CATALOG_SERVICE_ADDR=productcatalogservice:3550
Env SHIPPING_SERVICE_ADDR=shippingservice:50051
Env PAYMENT_SERVICE_ADDR=paymentservice:50051
Env EMAIL_SERVICE_ADDR=emailservice:8080
Env CURRENCY_SERVICE_ADDR=currencyservice:7000
Env CART_SERVICE_ADDR=cartservice:7070

EXPOSE 5050

ENTRYPOINT ["/app/checkoutservice"]
