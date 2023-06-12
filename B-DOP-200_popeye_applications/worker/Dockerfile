FROM maven:3.8.4-jdk-11-slim as builder

WORKDIR /src

COPY pom.xml .
RUN mvn dependency:resolve

COPY /src .
RUN mvn package

FROM openjdk:11-jre-slim

COPY --from=builder /src/target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]
