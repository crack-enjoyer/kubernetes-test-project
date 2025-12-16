# Используем официальный Node.js образ
FROM node:18-alpine

# Устанавливаем рабочую директорию
WORKDIR /app

# Копируем package.json и package-lock.json
COPY package*.json ./

# Устанавливаем зависимости
RUN npm ci --only=production

# Копируем исходный код приложения
COPY . .

# Открываем порт 3000
EXPOSE 3000

# Создаем non-root пользователя для безопасности
RUN addgroup -g 1001 -S nodejs && \
    adduser -S nodejs -u 1001

# Переключаемся на non-root пользователя
USER nodejs

# Запускаем приложение
CMD ["node", "server.js"]