FROM maven:3.8.5-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
# Entramos a la carpeta donde está el pom.xml
RUN cd Springboot-API-REST-DESPACHO && mvn clean package -DskipTests

FROM eclipse-temurin:17-jdk-focal
WORKDIR /app
COPY --from=build /app/Springboot-API-REST-DESPACHO/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]