# Use an official Maven image as a build stage
FROM maven as build

# Set the working directory for the build stage
WORKDIR /app

# Copy only the Maven project files needed for building

# Build the Maven project
RUN mvn clean install

# Use an official Python runtime as a base image
FROM python:3.8-slim

# Update the package list and install python3
RUN apt-get update && \
    apt-get install -y python3

RUN mkdir -p /app
WORKDIR /app

COPY . .


EXPOSE 8080


# Run launch.py when the container launches
CMD ["python", "python-app/launch.py"]
