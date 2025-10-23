FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
ARG NEXT_PUBLIC_BASE_PATH
ENV NEXT_PUBLIC_BASE_PATH=$NEXT_PUBLIC_BASE_PATH
RUN npm run build

FROM node:18-alpine
WORKDIR /app
COPY --from=build /app ./
EXPOSE 3000
CMD ["npm", "start"]