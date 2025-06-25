FROM node:16-alpine
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx

RUN rm -rf /etc/nginx/conf.d

COPY default.conf /etc/nginx/conf.d

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 3000