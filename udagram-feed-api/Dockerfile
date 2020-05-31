FROM node:11 AS builder
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build


FROM node:11
WORKDIR /usr/src/app
COPY package*.json ./
ENV NODE_ENV=production
RUN npm ci
COPY --from=builder /usr/src/app/www/ ./
EXPOSE 8081
CMD ["node", "server.js"]
