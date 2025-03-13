#---stage 1------
FROM node:alpine as build
WORKDIR /app
COPY package*.json . /
RUN npm install --production
COPY . .
RUN npm run build
#-----stage 2------
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]