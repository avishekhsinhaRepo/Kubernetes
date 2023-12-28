FROM docker.repo1.uhc.com/gov-prog-digital/gpd-node19-alpine:latest as builder

RUN npm config set registry http://repo1.uhc.com/artifactory/api/npm/npm-virtual

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN npm run build

FROM nginx:1.19-alpine

COPY --from=builder /app/build /usr/share/nginx/html

COPY conf/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]