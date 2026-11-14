# ETAPA 1 - Construir a aplicação React/Vite
FROM node:24-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

# ETAPA 2 - Servir o frontend com Nginx
FROM nginx:alpine

COPY --from=build /app/dist /usr/share/nginx/html

# Configura o proxy reverso
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]