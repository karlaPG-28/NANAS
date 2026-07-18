# Etapa 1: Construcción
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .
# Entramos a la ruta profunda donde está el pom.xml y compilamos
RUN cd demo/demo && mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM eclipse-temurin:17-jdk-alpine
# Copiamos el .jar desde la ruta profunda donde Maven lo generó
COPY --from=build /app/demo/demo/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]