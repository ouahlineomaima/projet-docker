FROM node:16.18.1-alpine AS builder
ENV CLOUDL_SERVER=localhost
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
FROM nginx:1.23.2-alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=builder /usr/src/app/build .
COPY --from=builder /usr/src/app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]