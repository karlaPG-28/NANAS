# Etapa 1: Construcción (usamos Maven con Java 21)
FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app
COPY . .
# Entramos a la ruta donde está el pom.xml y compilamos
RUN cd demo/demo && mvn clean package -DskipTests

# Etapa 2: Ejecución (usamos Java 21)
FROM eclipse-temurin:21-jdk-alpine
# Copiamos el .jar desde la ruta profunda
COPY --from=build /app/demo/demo/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]