# Frontend Dockerfile (Angular -> nginx)
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build --configuration=production || npx ng build --configuration=production

FROM nginx:1.27-alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf
# copy dist folder
COPY --from=builder /app/dist/angular-15-crud /usr/share/nginx/html
EXPOSE 80
