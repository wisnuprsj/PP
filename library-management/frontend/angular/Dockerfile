FROM node:14.21.2-alpine3.16 as build

WORKDIR /app

RUN npm install -g @angular/cli

COPY package.json .

RUN npm install

COPY . .

RUN ng build

FROM nginx as runtime

COPY --from=build /app/dist/frontend /usr/share/nginx/html

COPY conf/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD [ "nginx", "-g", "daemon off;" ]
