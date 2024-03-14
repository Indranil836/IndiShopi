# Stage 1
FROM node:21-alpine3.18 as build-stage

WORKDIR /client
COPY package.json .
RUN npm install
COPY . .

RUN npm run build

# Stage 2
FROM nginx:1.25.4

COPY --from=build-stage /client/build /usr/share/nginx/html
EXPOSE $REACT_DOCKER_PORT

CMD nginx -g 'daemon off;'
