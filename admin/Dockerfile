# Set the base image to Node 18-alpine3.18
FROM node:18-alpine3.18

# Set the working directory for all subsequent commands
WORKDIR /app/admin

# Copy the package.json and npm lock files to the working directory
COPY package.json .

RUN npm i -g npm@latest

# Run the apk update command to update package information
RUN apk update

# Install the dependencies
RUN npm i 
# --network-timeout 100000000

# Copy all files in the current directory (.) to the working directory in the container
COPY . .

# Run the npm build command to build the application
# RUN npm i vite
# RUN npm run build

# Set the default command to serve the built application
ENTRYPOINT [ "npm", "run", "dev"]