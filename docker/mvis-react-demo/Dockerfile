FROM node:13.12.0-alpine

# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

#Copies the source code 
COPY ./public ./public
COPY ./src ./src

# install app dependencies
COPY package.json ./
COPY package-lock.json ./

RUN npm install --silent

# Uses port which is used by the actual application
EXPOSE 3000

# start app
CMD ["npm", "start"]