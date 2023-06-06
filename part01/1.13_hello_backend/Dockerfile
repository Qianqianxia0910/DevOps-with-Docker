#use golang:1.16-alpine as builder
FROM golang:1.16-alpine 

#set working directory
WORKDIR /usr/src/app

#copy source files
COPY . .

#build the project
RUN go build



#expose port
EXPOSE 8080

#run the application
CMD ["./server"]
