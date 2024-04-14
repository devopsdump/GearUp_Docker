# Stage 1: Build the application
FROM node:14 AS build
# Set the working directory in the container
WORKDIR /usr/src/app
# Copy package.json and package-lock.json to the container
COPY package*.json ./
# Install dependencies
RUN npm install
# Copy the rest of the application code to the container
COPY . .
# Build the application
RUN npm run build
# Stage 2: Create a lightweight image to run the application
FROM node:14-alpine
# Set the working directory in the container
WORKDIR /usr/src/app
# Copy the build artifacts from the previous stage
COPY --from=build /usr/src/app ./
# Expose the port the app runs on
EXPOSE 3000
# Command to run the application
CMD ["npm", "start"]
