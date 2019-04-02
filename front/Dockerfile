FROM node:latest as node
WORKDIR /app
COPY package.json /app/
RUN npm i npm@latest -g
RUN npm install
COPY ./ /app/
ARG env=prod
RUN npm run build

FROM nginx:latest
COPY --from=node /app/dist/front /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf