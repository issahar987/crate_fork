# Use official Node.js image as the base image
FROM node:latest

# Set the working directory inside the container
WORKDIR /usr/src/app

# Clone the repository
RUN git clone https://github.com/issahar987/crate_fork.git crate

# Change directory to the cloned repository
WORKDIR /usr/src/app/crate/code/web

# Install npm packages
RUN npm install

# Install additional dependency
RUN npm install @babel/cli

# Update Browserslist DB
RUN npx browserslist@latest --update-db

# Set NODE_OPTIONS environment variable
ENV NODE_OPTIONS="--openssl-legacy-provider"

# Expose port 3000 for the web application
EXPOSE 3000

# Command to run the web application
# CMD ["npm", "start"]
# Command to run the web application in production mode
CMD ["npm", "run", "start:prod"]
