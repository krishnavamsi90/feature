# Stage 1: Build React application
FROM node:14-alpine as build

WORKDIR /app/frontend

COPY . .
RUN npm install

RUN npm run build

# Stage 2: Serve React application with Nginx
FROM nginx:alpine

COPY --from=build /app/frontend/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
