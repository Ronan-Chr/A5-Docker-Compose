# Use a Node.js base image for the build stage. You should use the node:18-alpine image.
FROM node:18-alpine AS build

# Set a working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies with npm install
RUN npm install

# Copy all the application files
COPY . .

# Build the production application with npm run build
RUN npm run build

# Use nginx to serve the built files (multi-stage build) with the command:
FROM nginx:alpine

# Copy build files from 
COPY --from=0 /app/dist /usr/share/nginx/html

# Expose port 80 (nginx default port)
EXPOSE 80

# Start nginx to serve the application with the command
CMD ["nginx", "-g", "daemon off;"]