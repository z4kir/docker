FROM node
 
WORKDIR /usr/src/app

COPY package*.json ./
 
RUN npm install -g serve
 
COPY . .
 
EXPOSE 3000
 
CMD [ "serve" ]