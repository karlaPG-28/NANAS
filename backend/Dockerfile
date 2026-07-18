# Etapa 1: Construcción
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
# Copiamos todo el contenido del repositorio
COPY . .
# Cambiamos al directorio 'backend' donde está el pom.xml y compilamos
RUN cd backend && mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM eclipse-temurin:17-jdk-alpine
# Copiamos el .jar resultante desde backend/target/ al directorio raíz
COPY --from=build /app/backend/target/*.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]