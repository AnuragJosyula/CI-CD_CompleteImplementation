# Use Java 17 base image
FROM eclipse-temurin:17-jdk-alpine

# Path to your built artifact
ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

COPY ${artifact} app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
