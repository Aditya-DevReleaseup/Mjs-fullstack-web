# Stage 1: Build React app with Node.js
FROM node:18 AS build 

# Set working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json for npm install
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all application files
COPY . ./

# Build the React app (you can replace `npm run build` with your specific build command if necessary)
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:latest  # Use official Nginx image

# Remove default nginx.conf provided by Nginx
RUN rm /etc/nginx/nginx.conf

# Copy custom nginx.conf
COPY nginx.conf /etc/nginx/nginx.conf

# Copy build artifacts from the first stage
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 for Nginx to listen on
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
