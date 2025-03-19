FROM node:18.17.0-alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build
COPY . .
EXPOSE 3000
CMD ["npm", "run", "start"]