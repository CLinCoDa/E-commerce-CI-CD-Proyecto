#Cliente dockerfile
# ETAPA 1: Construcción (Build)
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
# Instalación limpia para CI
RUN npm ci 
COPY . .
RUN npm run build

# ETAPA 2: Producción (Servidor estático)
FROM nginx:stable-alpine
# Copiamos solo los archivos compilados de la etapa anterior
COPY --from=build /app/build /usr/share/nginx/html
# Copiamos una configuración de nginx si la tuvieras, si no, usa la default
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]