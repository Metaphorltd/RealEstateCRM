# Use official Node.js LTS image
FROM node:18

# Set working directory
WORKDIR /app/server

# Copy server files
COPY . .
COPY ../package*.json /app/

# Install dependencies from root package.json
WORKDIR /app
RUN npm install

# Expose server port
EXPOSE 5001

# Set environment variables (override in docker-compose or at runtime)
ENV NODE_ENV=production

# Start the server
CMD ["node", "index.js"]
