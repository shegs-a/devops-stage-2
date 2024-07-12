# Use official Node.js image as the base image
FROM node:latest as build

# Set the working directory in the container
WORKDIR /app

# Copy the entire project to the working directory
COPY . /app

# Install dependencies
RUN npm install

# Expose port 5173
EXPOSE 5173

# Command to 
CMD [ "npm", "run", "dev", "--", "--host" ]