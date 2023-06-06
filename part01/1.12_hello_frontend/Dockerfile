# use an official ubuntu runtime as a parent image
FROM ubuntu:latest
# set the working directory inside the container
WORKDIR /usr/src/app

# copy the project source code inside the container
COPY . .

# install curl and nodejs
RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get install -y nodejs

RUN npm install
RUN npm run build
RUN npm install -g serve

# set the command to run the application
CMD ["serve", "-s", "-l", "5000","build"]

# Expose the port 
EXPOSE 5000