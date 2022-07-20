FROM node:14-alpine

# Add tool which will fix init process
RUN apk add dumb-init

# # Optimise for production
ENV NODE_ENV production

# Create app directory
USER node

WORKDIR /app
COPY ./package.json .

# # Copy app files
COPY --chown=node:node ./dist/apps/app-one .

# # Install only production dependencies
# RUN npm ci --only=production
RUN npm install --production

# # friends don’t let friends run containers as root!
# USER node

# WORKDIR /app

# COPY ./package.json .

# RUN npm install --production

# COPY ./dist/apps/app-one .

# Make port 8080 accessible outside of container
EXPOSE 3000
# CMD ["dumb-init", "node", "main.js" ]
CMD node ./main.js
