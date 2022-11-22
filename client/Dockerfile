FROM node:16-alpine AS builder

RUN mkdir -p /app/react
WORKDIR /app/react
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build


FROM nginx
EXPOSE 3000
COPY ./nginx/deafult.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/react/build /usr/share/nginx/html
