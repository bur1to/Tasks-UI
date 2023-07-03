FROM node:18.16.0

WORKDIR /app2

COPY package*.json ./

RUN npm install

COPY . .

CMD ["npm", "run", "serve"]
