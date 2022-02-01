FROM node:16-alpine3.14 as build

WORKDIR /opt/app

COPY ./package.json .

RUN npm i

COPY . .

RUN npm run build

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /opt/app/build /usr/share/nginx/html
