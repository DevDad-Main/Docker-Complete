FROM node:24

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

#INFO: We place it after the above so we don't have to re-check everything above just because i changed the port number for e.g. -> the top is already cached so we skip those layers

# This is a bit of inception what we are doing below but it just shows off how we can use the build time args and then use them as variables in place for other ENV vars for e.g

#NOTE: We can then have different images for different environments - dev, test, prod etc
# For Web Image: docker build -t feedback-node:web .
# For Dev Image: docker build -t feedback-node:dev --build-arg DEFAULT_PORT=3000 . -> We can specify this build time arg and change it for our Development environment
ARG DEFAULT_PORT=80

ENV PORT=${DEFAULT_PORT}

# We have to use the $PORT variable to get the port number from the environment variable

# Instead of specifying everything here we can put all our variables in an .env and add that to our docker run command like so
# -e PORT=8000 - Singular flag
# Full Command: docker run -d --rm -p 3000:80 --env-file ./.env --name feedback-app -v feedback:/app/feedback -v "$(pwd)":/app:ro -v /app/temp -v /app/node_modules feedback-node:env

EXPOSE $PORT

#FIX: anonymous volume - Need to change to named volumes so our data persists correctly

# We have to create the named volume when we create our container with the -v flag
# VOLUME ["/app/feedback"]

# NOTE: we now use a bind mount to map the feedback directory to our container directory so we can have persistent updates of our code without having to rebuild the imges and make a new contianer each time. Issue we had is due to it overwritting everything inside with our code on the outside we then got an error becuase express wasn't installed - due to us not building our package.json.
# NOTE: This is a good example of why we use an anoynmous volume so that we don't overwrite the node_modules but use the one inside the container instead.

# docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v "$(pwd)":/app -v /app/node_modules feedback-node:named-vol

# We can also define the :ro read only flag to ensure that the data inside if we modify anything it dosent make chnges on the outside - so we cotnain everyting in our container as by default bing mounts have R/W access.

# docker run -d --rm -p 3000:80 --name feedback-app -v feedback:/app/feedback -v "$(pwd)":/app:ro -v /app/temp -v /app/node_modules feedback-node:volumes

#NOTE: We dont us our anonymous volumes like this - we need to define them in the command and we make our bind mount to really ensure that it override the bind mount.
# VOLUME ["/app/node_modules"]
# VOLUME ["/app/temp"]

# CMD ["node", "server.js"]

# Utilizing the nodemon package
CMD ["npm", "start"]
