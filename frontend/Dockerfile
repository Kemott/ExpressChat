FROM node:14 AS build-step

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

#RUN npm ci --only=production

COPY . .

RUN npm run build

EXPOSE 4200

FROM nginx:1.17.1-alpine

COPY --from=build-step /dist/frontend /usr/share/nginx/html

