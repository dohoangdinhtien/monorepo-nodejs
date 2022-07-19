FROM node:14-alpine

# Add tool which will fix init process
RUN apk add dumb-init

# Optimise for production
ENV NODE_ENV production

# Create app directory
WORKDIR /usr/src/app

# Copy app files
COPY --chown=node:node ./dist/apps/app-one /usr/src/app

# Install only production dependencies
# RUN npm ci --only=production
RUN npm install

# friends don’t let friends run containers as root!
USER node

# Make port 8080 accessible outside of container
EXPOSE 3000
CMD ["dumb-init", "node", "main.js" ]
