# Use official Node.js image as the base image
FROM node:latest as build

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
# COPY package*.json ./
# Copy the entire project to the working directory
COPY . /app

# Install dependencies
RUN npm install

# Build the React app
# RUN npm run build

# Use lightweight Nginx image for serving the static files
# FROM nginx:1.21

# Copy the build output from the previous stage to Nginx public directory
# COPY --from=build /app/build /usr/share/nginx/html

# Expose port 5173
EXPOSE 5173

# Command to 
CMD [ "npm", "run", "dev", "--", "--host" ]