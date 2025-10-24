FROM node:24

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

#FIX: anonymous volume - Need to change to named volumes so our data persists correctly

# We have to create the named volume when we create our container with the -v flag
# VOLUME ["/app/feedback"]

# NOTE: we now use a bind mount to map the feedback directory to our container directory so we can have persistent updates of our code without having to rebuild the imges and make a new contianer each time. Issue we had is due to it overwritting everything inside with our code on the outside we then got an error becuase express wasn't installed - due to us not building our package.json.
# NOTE: This is a good example of why we use an anoynmous volume so that we don't overwrite the node_modules but use the one inside the container instead.

# docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v "$(pwd)":/app -v /app/node_modules feedback-node:named-vol

# CMD ["node", "server.js"]

# Utilizing the nodemon package
CMD ["npm", "start"]
