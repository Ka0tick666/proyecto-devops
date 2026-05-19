# Etapa 1: Compilación
FROM maven:3.8.5-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
# ENTRAMOS a la subcarpeta de Ventas
RUN cd Springboot-API-REST && mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM eclipse-temurin:17-jdk-focal
WORKDIR /app
COPY --from=build /app/Springboot-API-REST/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
