FROM node:21 as builder

WORKDIR /app/angular_exemple_1

COPY package*.json ./

RUN npm install -g @angular/cli

RUN npm install

COPY . .

RUN ng build 