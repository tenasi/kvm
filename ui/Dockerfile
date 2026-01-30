# Build Stage
FROM docker.io/node:22.21.1-alpine AS build
WORKDIR /app
COPY . /app
RUN npm ci
RUN ls /app/public
RUN npm run build:prod

# Run Stage
FROM docker.io/nginx:alpine
COPY --from=build /app/dist /var/www
COPY nginx.conf /etc/nginx/nginx.conf
