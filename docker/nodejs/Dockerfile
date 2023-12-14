# Dockerfile.build
FROM node:14 as builder

WORKDIR /home/source/main

COPY package*.json ./

RUN npm install

# CMD [ "npm", "install" ]

COPY . .

# Menjalankan perintah npm run dev
CMD ["npm", "run", "dev"]
