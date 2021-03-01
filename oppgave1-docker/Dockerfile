FROM maven:3.6-jdk-11 as builder

WORKDIR /app
COPY pom.xml .
COPY src ./src

RUN mvn package -DskipTests

FROM adoptopenjdk/openjdk11:alpine-slim
WORKDIR /app

COPY --from=builder /app/target/*.jar application.jar
COPY index.html .
ENTRYPOINT ["java","-jar","application.jar"]