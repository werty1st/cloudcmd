FROM node:lts-buster
LABEL maintainer="Coderaiser"

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY package.json /usr/src/app/

RUN apt-get update && \
    npm config set package-lock false && \
    npm install --production && \
    npm i gritty && \
    npm cache clean --force && \
    apt-get clean

COPY . /usr/src/app

WORKDIR /

ENV cloudcmd_terminal true \
    cloudcmd_terminal_path gritty \
    cloudcmd_open false

EXPOSE 8000

ENTRYPOINT ["/usr/src/app/bin/cloudcmd.mjs"]
