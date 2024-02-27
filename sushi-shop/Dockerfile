# Используйте минимальный образ Node.js
FROM node:21.6.2 as builder

# Установка зависимостей
WORKDIR /app
COPY package*.json ./
RUN npm install


COPY . .
RUN npm run build

# Создание образа Nginx для раздачи статических файлов
FROM nginx:1.21.3-alpine
COPY --from=builder /app/dist /usr/share/nginx/html

# Открытие порта 80 для веб-сервера Nginx
EXPOSE 80

# Команда для запуска Nginx в фоновом режиме
CMD ["nginx", "-g", "daemon off;"]