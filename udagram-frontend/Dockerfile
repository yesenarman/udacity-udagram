FROM node:10 AS builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build


FROM trion/nginx-angular
COPY --from=builder /usr/src/app/www /usr/share/nginx/html
