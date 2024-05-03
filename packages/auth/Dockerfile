FROM node:18-slim

WORKDIR /app

RUN apt-get update && apt-get upgrade -y

USER node

COPY *.json .
COPY yarn.lock .

COPY packages/commons /app/packages/commons
RUN cd packages/commons && yarn install && yarn build

COPY packages/auth /app/packages/auth
RUN cd packages/auth && yarn install && yarn build

WORKDIR /app/packages/auth

CMD ["yarn", "start:prod"]
