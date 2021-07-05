#FROM node
#WORKDIR /usr/src/app
#COPY package*.json ./
#RUN npm install
#COPY . .
#EXPOSE 8080
#CMD [ "node", "index.js" ]

FROM node:lts-alpine
RUN mkdir -p /home/node/app/node_modules && chown -R node:node /home/node/app
USER node
WORKDIR /home/node/app
COPY --chown=node:node package*.json ./
RUN npm install
COPY --chown=node:node . .
EXPOSE 8080
HEALTHCHECK --interval=12s --timeout=12s --start-period=30s CMD node healthcheck.js
CMD  chown -R node /home/node/app && node index.js
