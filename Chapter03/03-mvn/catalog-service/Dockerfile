#FROM openjdk:17-jdk-slim-buster
FROM openjdk:17-jdk-alpine

COPY target/catalog-service-0.0.1-SNAPSHOT.jar catalog-service-0.0.1-SNAPSHOT.jar

ENTRYPOINT ["java", "-jar", "/catalog-service-0.0.1-SNAPSHOT.jar"]