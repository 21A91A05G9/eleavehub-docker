# Stage 1: Build Stage
FROM node:lts-buster-slim AS development

# Set working directory
WORKDIR /app

# Copy dependency definitions
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy the rest of the application code
COPY . .

# Stage 2: Final Stage with a Minimal Image
FROM node:lts-buster-slim

# Set working directory
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=development /app /app

# Expose the application port
EXPOSE 3000

# Run the application
CMD ["npm", "start"]
