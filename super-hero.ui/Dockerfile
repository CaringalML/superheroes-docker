# Stage 1: Build Angular app
FROM node:16.14-alpine as build

# Set the working directory
WORKDIR /usr/src/app

# Copy only the package files first to leverage Docker cache
COPY package*.json ./

# Install Angular CLI globally
RUN npm install -g @angular/cli@14

# Install project dependencies using npm ci
RUN npm ci

# Copy the application files to the working directory
COPY . .

# Build the Angular app
RUN npm run build

# Stage 2: Use a smaller base image for the final container
FROM nginx:1.21.3-alpine

# Set the working directory
WORKDIR /usr/share/nginx/html

# Copy only the necessary build artifacts from the build stage
COPY --from=build /usr/src/app/dist/super-hero.ui .

# Expose port 80
EXPOSE 80

# Start NGINX in the foreground
CMD ["nginx", "-g", "daemon off;"]