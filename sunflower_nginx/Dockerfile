FROM node:8-alpine as sunflower_client

RUN mkdir -p /sunflower_client
WORKDIR /sunflower_client

COPY ./sunflower_client/package.json .
COPY ./sunflower_client/yarn.lock .

RUN yarn install

ADD ./sunflower_client/ .

RUN yarn build


FROM nginx:1.15-alpine

WORKDIR /

# Copy sunflower_client dist to nginx
COPY --from=sunflower_client /sunflower_client/dist /usr/share/nginx/html/dist

# Copy configuration files to the container
COPY ./sunflower_nginx/conf.d/local.conf /etc/nginx/conf.d/default.conf
