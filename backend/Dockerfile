#Alpine base image 18-alpine
FROM node:18-alpine

# Set working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./

# Install dependencies for backend
RUN npm install

# Copy backend source code for docker build
COPY . .

# create a DIR for the databbase files
RUN mkdir -p /app/db

#The endend API will be on port on 5000 like the assignment states
EXPOSE 5000

#Starts 
CMD ["npm", "start"]