FROM node:20.11.1-alpine as base

From base as builder

WORKDIR /app

COPY package*.json .

RUN npm install

##################

FROM base

WORKDIR /app

COPY --from=builder /app/node_modules /app/node_modules

COPY . .

#ENV SHIPPING_SERVICE_ADDR=shippingservice:50051

EXPOSE 50051

ENTRYPOINT [ "node", "index.js" ]