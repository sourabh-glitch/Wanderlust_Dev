# frontend/Dockerfile
# Stage 1: Build
FROM node:20-alpine AS build

WORKDIR /app

# Copy package.json and package-lock.json first (better caching)
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Build Vite production bundle
RUN npm run build

# Stage 2: Serve
FROM node:20-alpine

WORKDIR /app

# Install serve to serve static files
RUN npm install -g serve

# Copy built frontend
COPY --from=build /app/dist ./dist

# Expose port
EXPOSE 4173

# Command to serve frontend
CMD ["serve", "-s", "dist", "-l", "4173"]
