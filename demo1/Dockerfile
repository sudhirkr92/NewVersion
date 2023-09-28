# Stage 1: Build Stage
FROM eclipse-temurin:8-jdk-jammy as BUILD
WORKDIR /opt/app
COPY .mvn/ .mvn
COPY mvnw pom.xml ./
RUN ./mvnw dependency:go-offline
COPY ./src ./src
RUN ./mvnw clean install
FROM eclipse-temurin:8-jre-jammy
WORKDIR /opt/app
EXPOSE 8085
COPY --from=BUILD /opt/app/target/*.jar /opt/app/*.jar
