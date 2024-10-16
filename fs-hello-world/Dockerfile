FROM node:20

# Node.js app lives here
WORKDIR /usr/src/app

# Install pnpm
ARG PNPM_VERSION=9.12.0
RUN npm install -g pnpm@$PNPM_VERSION

# Copy application code
COPY . .

# Start the server by default, this can be overwritten at runtime
CMD DEBUG=fs-hello-world:* pnpm start