# Etapa 1: Compilación
FROM maven:3.8.5-eclipse-temurin-17 AS build
WORKDIR /app
# Copiamos todo
COPY . .
# ENTRAMOS a la subcarpeta antes de compilar (Ajusta el nombre si varía)
RUN cd Springboot-API-REST-DESPACHO && mvn clean package -DskipTests

# Etapa 2: Ejecución
FROM eclipse-temurin:17-jdk-focal
WORKDIR /app
# Buscamos el jar dentro de la subcarpeta/target
COPY --from=build /app/Springboot-API-REST-DESPACHO/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]