FROM docker.repo1.uhc.com/gov-prog-digital/gpd-node19-alpine:latest

RUN npm config set registry http://repo1.uhc.com/artifactory/api/npm/npm-virtual

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

CMD [ "node", "auth-app.js" ]