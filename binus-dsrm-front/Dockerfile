# Base image: Node LTS (aman & stabil)
FROM node:18

# Set working directory
WORKDIR /app

# Salin package info dulu (biar caching install lebih efisien)
COPY package*.json ./

# Install deps
RUN npm install

# Salin semua kode
COPY . .

# Expose port default Vite
EXPOSE 5173

# Jalankan dev server
CMD ["npm", "run", "dev"]
