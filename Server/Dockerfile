# Usamos una imagen ligera de Java 17
FROM eclipse-temurin:17-jre-alpine

WORKDIR /app

# Argumento para el nombre del archivo JAR (da flexibilidad)
ARG JAR_FILE=target/organica-0.0.1-SNAPSHOT.jar

# Copiamos el archivo generado por Maven al contenedor
COPY ${JAR_FILE} app.jar

# Exponemos el puerto que definiste en el docker-compose
EXPOSE 9090

# Optimización de memoria para contenedores
ENTRYPOINT ["java", "-Xmx512m", "-Xms256m", "-jar", "app.jar"]