FROM node:21 as builder

WORKDIR /app

COPY package*.json ./

RUN npm install -g @angular/cli

RUN npm install

COPY . .


CMD [ "ng", "build", "--verbose" ]
# CMD [ "ng", "serve", "--host", "0.0.0.0", "--port", "4200" ]