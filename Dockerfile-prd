# syntax=docker/dockerfile:experimental
FROM node:12.16.1-alpine3.11 as builder 

WORKDIR /app

COPY . .

RUN --mount=type=cache,target=/app/node_modules \
    --mount=type=cache,target=/root/.npm \
    npm install \
    && npm run build

FROM nginx:1.16.1-alpine

COPY --from=builder /app/build /usr/share/nginx/html
