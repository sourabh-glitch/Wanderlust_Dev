# backend/Dockerfile
FROM node:20-alpine

WORKDIR /app

# Copy package.json first for caching
COPY package*.json ./
RUN npm install --production

# Copy backend code
COPY . .

# Expose backend port
EXPOSE 8080

# Start backend
CMD ["node", "index.js"]
