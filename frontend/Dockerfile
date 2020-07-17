FROM node:alpine

RUN apk add --no-cache libc6-compat
ENV NODE_ENV development
ENV PORT 3000
EXPOSE 3000

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY package*.json /usr/src/app/
RUN npm install --no-optional

COPY . /usr/src/app

RUN npm run build
RUN npx next telemetry disable

CMD "npm" "run" "dev"
