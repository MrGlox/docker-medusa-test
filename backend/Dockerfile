# Set the base image to Node 18-alpine3.18
FROM node:18-alpine3.18

# Set the working directory
WORKDIR /app/medusa

# Copy the necessary files
COPY package.json .
COPY develop.sh .

# Run the apk update command to update package information
RUN apk update

RUN npm i -g npm@latest

# Install dependencies
RUN npm i 
# --network-timeout 100000000

# Install the medusa-cli
RUN npm i -g @medusajs/medusa-cli@latest

# Add the remaining files
COPY . .

# Set the default command to run when the container starts
ENTRYPOINT ["sh", "develop.sh"]