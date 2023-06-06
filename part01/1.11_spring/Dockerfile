# Use an official Java 8 runtime as the base image
FROM openjdk:8-jdk-alpine

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy the project source code inside the container
COPY . .

# Build the project with Maven Wrapper
RUN ./mvnw package 

# Set the command to run the application
CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]

# Expose the port on which the application is running
EXPOSE 8080


