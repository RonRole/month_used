FROM node:latest
WORKDIR /usr/src/front
RUN npm update -g npm
RUN yarn global add @vue/cli
COPY . .
RUN yarn
RUN umask 0001
