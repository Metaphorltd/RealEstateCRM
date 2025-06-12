# Use official Node.js LTS image for build
FROM node:18.16.0 as build

WORKDIR /app

COPY package*.json ./
RUN npm install
ENV NODE_OPTIONS=--max_old_space_size=4096

ARG REACT_APP_BASE_URL=http://localhost:5001/
ENV REACT_APP_BASE_URL=$REACT_APP_BASE_URL

COPY . .
RUN npm run build

# Use nginx to serve the build
FROM nginx:alpine

# Add custom nginx config for SPA routing
COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build /app/build /usr/share/nginx/html

# Expose default nginx port
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
