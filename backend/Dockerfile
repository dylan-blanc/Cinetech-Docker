# syntax=docker/dockerfile:1

FROM node:26.2-alpine AS base
WORKDIR /app
COPY package*.json ./
RUN npm ci

FROM base AS dev
ENV NODE_ENV=development
COPY . .
EXPOSE 3500
CMD ["npm", "run", "dev"]

FROM node:26.2-alpine AS prod
WORKDIR /app
ENV NODE_ENV=production
COPY package*.json ./
RUN npm ci --omit=dev
COPY . .
EXPOSE 3500
CMD ["npm", "start"]
