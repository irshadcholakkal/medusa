# FROM node:20-alpine
# WORKDIR /app
# COPY package.json package-lock.json ./
# RUN npm install
# COPY . .
# EXPOSE 9000
# CMD ["npm", "run", "dev"]

FROM node:20-slim AS deps
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci

FROM node:20-slim
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .
EXPOSE 9000
CMD ["npm", "run", "start"]
