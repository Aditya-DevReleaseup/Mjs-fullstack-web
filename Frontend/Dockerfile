# Step 1: Build the React app
FROM node:16 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy the rest of the app source code
COPY . ./

# Build the React app
RUN npm run build

# Step 2: Serve with Nginx
FROM nginx:alpine

# Copy the build files from the previous build stage to Nginx's web server directory
COPY --from=build /app/build /usr/share/nginx/html

# Copy custom nginx.conf to replace the default one
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80 to access the React app
EXPOSE 80

# Run Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
