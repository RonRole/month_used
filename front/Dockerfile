FROM node:latest
WORKDIR /usr/src/front
RUN npm update -g npm
RUN npm -g yarn
RUN yarn global add @vue/cli
COPY . .
RUN yarn update
RUN umask 0001