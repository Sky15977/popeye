FROM maven:3.8.4-jdk-11-slim as builder

WORKDIR /test

COPY pom.xml .
RUN mvn dependency:resolve

COPY ./src/ /test/src/
RUN mvn package

FROM openjdk:11-jre-slim

COPY --from=builder /test/target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]
