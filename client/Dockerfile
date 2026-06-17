FROM node:18-alpine As Builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install
COPY . .

# Build the production React app
RUN npm run build

# ---- Stage 2: Serve with Nginx ---
FROM nginx:alpine
COPY --from=Builder /app/build /usr/share/nginx/html

# Expose port 80 to the outside
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]