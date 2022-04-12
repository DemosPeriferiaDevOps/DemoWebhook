FROM node:16-alpine3.14 as build-step

RUN mkdir -p /app

WORKDIR /app

COPY package.json /app

RUN yarn install

COPY . /app

RUN npm run build --prod

FROM nginx:1.21.6-alpine

COPY --from=build-step /app/dist/ /usr/share/nginx/html

EXPOSE 80
EXPOSE 4200