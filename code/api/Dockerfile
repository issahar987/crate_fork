# Use official Node.js image as the base image
FROM node:latest

# Set the working directory inside the container
WORKDIR /usr/src/app

# Clone the repository
RUN git clone https://github.com/issahar987/crate_fork.git crate

# Switch to code directory
WORKDIR /usr/src/app/crate/code

# Copy database configuration
COPY my_database.json api/src/config/database.json

# Switch to api directory
WORKDIR /usr/src/app/crate/code/api

# Install npm packages
RUN npm install

# Install pg
RUN npm install pg

# Update Browserslist DB
RUN npx browserslist@latest --update-db

# Set NODE_OPTIONS environment variable
ENV NODE_OPTIONS="--openssl-legacy-provider"

# Setup database (migrations and seed)
RUN npm run setup

# Expose port 8000 for the API
EXPOSE 8000

# Command to run the API in production mode
CMD ["npm", "run", "start:prod"]
