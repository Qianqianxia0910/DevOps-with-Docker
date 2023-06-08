# part01

## 1.1

docker ps -a

```shell
CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS                     PORTS     NAMES
68f96cee1573   nginx         "/docker-entrypoint.…"   4 minutes ago   Up 4 minutes               80/tcp    kind_chaplygin
41b560b44a55   nginx         "/docker-entrypoint.…"   4 minutes ago   Exited (0) 3 minutes ago             eager_mendel
6887180d7822   nginx         "/docker-entrypoint.…"   6 minutes ago   Exited (0) 3 minutes ago             stoic_elbakyan
```

## 1.2

docker ps -a

```shell
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

docker images

```shell
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

## 1.3

```shell
Secret message is: 'You can find the source code here: https://github.com/docker-hy'
```

commands

```shell
docker run -d devopsdockeruh/simple-web-service:ubuntu
docker ps
docker exec -it relaxed_colden bash
ls 
cat text.log
```

## 1.4

commands

```shell
docker run -d -it ubuntu sh -c 'while true; do echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website; done'

docker ps

docker exec -it quirky_bose bash

apt-get update
apt-get install curl
curl helsinki.fi
```

## 1.5

sizes of images

```shell
ubuntu: 83MB
alpine: 15.7MB
```

commands and output

```shell
docker pull devopsdockeruh/simple-web-service:ubuntu
docker pull devopsdockeruh/simple-web-service:alpine

docker image ls

docker run -d -it devopsdockeruh/simple-web-service:ubuntu
docker run -d -it devopsdockeruh/simple-web-service:alpine

docker ps

docker exec -it inspiring_pare bash
tail -f ./text.log
Secret message is: 'You can find the source code here: https://github.com/docker-hy'

docker exec -it cool_gould sh
tail -f ./text.log
Secret message is: 'You can find the source code here: https://github.com/docker-hy'

```

## 1.6

commands and secret message

```shell
docker run -it devopsdockeruh/pull_exercise
Give me the password: basics

"This is the secret message"
```

## 1.7

Dockerfile

```shell
FROM ubuntu:20.04

WORKDIR /usr/src/app

COPY script.sh .

RUN apt-get update && apt-get install -y curl
RUN chmod +x script.sh

CMD ./script.sh
```

## 1.8

Dockerfile

```shell
FROM devopsdockeruh/simple-web-service:alpine

CMD ["server"]
```

commands

```shell
docker build . -t web-server

docker run web-server
```

## 1.9

commands

```shell
touch text.log
docker run -v "$(pwd)/text.log:/usr/src/app/text.log" devopsdockeruh/simple-web-service
```

## 1.10

commands

```shell
docker build . -t web-server

docker run -p 8080:8080 web-server
```

## 1.11

Dockerfile

```shell

FROM openjdk:8-jdk-alpine

WORKDIR /usr/src/app

COPY . .

RUN ./mvnw package 

CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]

EXPOSE 8080
```

## 1.12(MANDATORY EXERCISE)

Dockerfile

```shell
FROM ubuntu:latest

WORKDIR /usr/src/app

COPY . .

RUN apt-get update && apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get install -y nodejs

RUN npm install
RUN npm run build
RUN npm install -g serve

CMD ["serve", "-s", "-l", "5000","build"]

EXPOSE 5000
```

## 1.13(MANDATORY EXERCISE)

Dockerfile

```shell
FROM golang:1.16-alpine 

WORKDIR /usr/src/app

COPY . .

RUN go build

EXPOSE 8080

CMD ["./server"]
```

commands

```shell
git clone https://github.com/docker-hy/material-applications.git
cd  material-applications/example-backend/
docker build . -t example-backend
docker run -p 8080:8080 example-backend
```

## 1.14(MANDATORY EXERCISE)

Dockerfile example-frontend

```shell
FROM node:16

EXPOSE 5000

WORKDIR /usr/src/app

COPY . .

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN npm install
RUN npm run build
RUN npm install -g serve

CMD ["serve", "-s", "-l", "5000","build"]
```

Dockerfile example-backend

```shell
FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV REQUEST_ORIGIN=http://localhost:5000

RUN go build

CMD ["./server"]
```

commands

```shell
docker build . -t example-backend
docker run -p 8080:8080 example-backend
docker build . -t example-frontend
docker run -p 5000:5000 example-frontend
```

## 1.15

Link to the project in Docker Hub:<https://hub.docker.com/r/summerhkvb/first_project/tags>

This is the expree-app project from <https://github.com/docker-hy/material-applications.git>

Run the project using the following commands:

```shell
docker pull summerhkvb/first_project:latest
```
