# Etapa 1: Construcción
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM eclipse-temurin:17-jdk-alpine
COPY --from=build /app/backend/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]