# Use the Maven image as a build stage
FROM maven:3.-jdk-11-slim 

# Set up authentication for private Maven repository if needed
# RUN echo "<your-username>:<your-password>" > /root/.m2/settings-security.xml
# COPY settings.xml /root/.m2/

WORKDIR /home/app
COPY . /home/app/
RUN mvn -f /home/app/pom.xml clean package

# Use the OpenJDK image as the final image
FROM openjdk:8-jdk-alpine

# Copy the built artifact from the build stage
COPY --from=build /home/app/target/demo-0.0.1-SNAPSHOT.jar /app/demo-0.0.1-SNAPSHOT.jar

# Set the working directory
WORKDIR /app

# Command to run the application
CMD ["java", "-jar", "demo-0.0.1-SNAPSHOT.jar"]
