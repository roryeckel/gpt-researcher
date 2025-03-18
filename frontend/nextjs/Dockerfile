FROM node:18.17.0-alpine as builder
WORKDIR /app
COPY ./package.json ./
COPY ./package-lock.json ./ 
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build
RUN npm run export

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/out /usr/share/nginx/html