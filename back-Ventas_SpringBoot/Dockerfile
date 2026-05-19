# Etapa 1: Construcción
FROM maven:3.8.5-openjdk-17 AS builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Etapa 2: Ejecución (Seguridad: Usuario no root)
FROM openjdk:17-jdk-slim
WORKDIR /app
RUN addgroup --system devopsgroup && adduser --system devopsuser --ingroup devopsgroup
USER devopsuser
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]