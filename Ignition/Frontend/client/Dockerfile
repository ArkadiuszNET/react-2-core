#Build app

FROM node:alpine AS build

WORKDIR /app

ARG REACT_APP_NAME
ENV REACT_APP_NAME $REACT_APP_NAME

COPY package.json .
COPY yarn.lock .

RUN yarn install

COPY . .

RUN yarn build


#Run

FROM nginx:stable-alpine

COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx","-g", "daemon off;"]