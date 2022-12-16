# syntax=docker/dockerfile:1
FROM node:19.1.0-alpine3.16
ENV NODE_ENV=production
WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]
RUN npm install --production
COPY . .
EXPOSE 80
CMD [ "node", "server.js" ]