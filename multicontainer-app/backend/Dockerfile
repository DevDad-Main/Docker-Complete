FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

# ENV MONGODB_USERNAME=root
# ENV MONGODB_PASSWORD=secret

# Changed the command to now utilize nodemon so we can see the live changes in our web app
CMD ["npm", "start"]
