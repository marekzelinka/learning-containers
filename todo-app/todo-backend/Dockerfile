# syntax = docker/dockerfile:1

# Adjust NODE_VERSION as desired
ARG NODE_VERSION=20.16.0
FROM node:${NODE_VERSION}-slim AS base

# Node.js app lives here
WORKDIR /usr/src/app

# Set production environment
ENV NODE_ENV="production"

# Install packages needed to build node modules
RUN apt-get update -qq && \
    apt-get install --no-install-recommends -y build-essential node-gyp pkg-config python-is-python3

# Install node modules
COPY package.json package-lock.json ./
RUN npm install --frozen-lockfile --prod=false

# Copy application code
COPY . .

# Remove development dependencies
RUN npm prune --prod

# Show all internal logs used in Express
ENV DEBUG=express:*

# Start the server by default, this can be overwritten at runtime
EXPOSE 3000
CMD [ "npm", "run", "start" ]