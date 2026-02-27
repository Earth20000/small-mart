# Stage 1: Build the React client
FROM node:20-alpine AS client-builder

WORKDIR /app/client

# Copy client package files
COPY client/package*.json ./

# Install all dependencies (including devDependencies for build)
RUN npm install --legacy-peer-deps

# Install missing babel plugin
RUN npm install @babel/plugin-proposal-private-property-in-object --save-dev

# Copy client source code
COPY client/ ./

# Set CI=false to treat warnings as warnings, not errors
ENV CI=false

# Build the React app for production
RUN npm run build

# Stage 2: Build the production image
FROM node:20-alpine AS production

WORKDIR /app

# Copy server package files
COPY package*.json ./

# Install only production dependencies
RUN npm install --only=production

# Copy server source code
COPY server.js ./
COPY config/ ./config/
COPY controllers/ ./controllers/
COPY helpers/ ./helpers/
COPY middlewares/ ./middlewares/
COPY models/ ./models/
COPY routes/ ./routes/

# Copy built React app from client-builder stage
COPY --from=client-builder /app/client/build ./client/build

# Expose the port
EXPOSE 8080

# Set environment variables
ENV NODE_ENV=production
ENV PORT=8080

# Start the server
CMD ["node", "server.js"]
