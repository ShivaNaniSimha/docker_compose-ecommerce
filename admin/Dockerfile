FROM node:18.18.1 AS build
WORKDIR /app
COPY  package*.json ./
RUN npm i
 
COPY . .
RUN npm run build

FROM nginx:alpine  
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=build /app/dist .
EXPOSE 80
CMD [ "nginx","-g","daemon off;" ]
