
# Étape 1 : Construction de l'application
FROM maven:latest as build

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier pom.xml et le répertoire src
COPY pom.xml .
COPY src ./src

# Construire l'application
RUN mvn clean package -DskipTests

FROM openjdk:17


# Définir le répertoire de travail
WORKDIR /app

ENV SPRING_APPLICATION_NAME="service-proxy"
ENV SPRING_CLOUD_CONFIG_URI="http://service-config:8080"
ENV SPRING_CONFIG_IMPORT="configserver:http://service-config:8080"


# Copier le JAR construit depuis l'étape de construction
COPY --from=build /app/target/*.jar app.jar

# Exposer le port de l'application
EXPOSE 8079

# Commande pour exécuter l'application
ENTRYPOINT ["java", "-jar", "app.jar"]