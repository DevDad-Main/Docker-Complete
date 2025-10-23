FROM node:24

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

#FIX: anonymous volume - Need to change to named volumes so our data persists correctly

# We have to create the named volume when we create our container with the -v flag
# VOLUME ["/app/feedback"]

CMD ["node", "server.js"]
