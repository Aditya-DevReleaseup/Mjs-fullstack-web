# Use an official Node.js runtime as a base image
FROM node:18-slim

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and package-lock.json (if present) into the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code into the container
COPY . .

# Expose the port your app will run on
EXPOSE 3000

# Set environment variable for production or development
# You can adjust the NODE_ENV as needed
ENV NODE_ENV=production

# Run the application (start in dev or prod mode based on your needs)
CMD ["npm", "run", "dev"]
