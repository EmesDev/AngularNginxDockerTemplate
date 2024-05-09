FROM node:21 as builder

WORKDIR /app

COPY package*.json ./

RUN npm install -g @angular/cli

RUN npm install

COPY . .

CMD [ "ng", "build", "--verbose" ]
