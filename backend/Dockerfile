# Use an official Node 18 Alpine runtime as the parent image
FROM node:20-slim AS base

ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"

RUN corepack enable

# Set the working directory in the container
WORKDIR /usr/src/app

# Install pnpm
RUN pnpm add @medusajs/medusa-cli -g

# Copy package.json and pnpm-lock.yaml
COPY package.json pnpm-lock.yaml ./

# Install any needed packages
RUN pnpm install --frozen-lockfile --shamefully-hoist

# Bundle app source
COPY . .

# Make port 9000 available to the world outside this container
EXPOSE 9000
EXPOSE 7001

# Define environment variables
# ENV NODE_ENV production

RUN medusa migrations run
RUN medusa seed 

# Run the app
CMD ["pnpm", "dev"]
