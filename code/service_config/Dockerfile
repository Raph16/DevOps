#
## Étape 1 : Construction de l'application
#FROM maven:latest as build
#
## Définir le répertoire de travail
#WORKDIR /app
#
## Copier le fichier pom.xml et le répertoire src
#COPY pom.xml .
#COPY src ./src
#
## Construire l'application
#RUN mvn clean package -DskipTests
#
#FROM openjdk:17
#
#
## Définir le répertoire de travail
#WORKDIR /app
#
## Copier le JAR construit depuis l'étape de construction
#COPY --from=build /app/target/*.jar app.jar
#
## Exposer le port de l'application
#EXPOSE 8080
#
## Commande pour exécuter l'application
#ENTRYPOINT ["java", "-jar", "app.jar"]

# Étape 1 : Construction de l'application
FROM maven:latest as build

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier pom.xml et le répertoire src
COPY pom.xml .
COPY src ./src

# Construire l'application
RUN mvn clean package -DskipTests

# Étape 2 : Exécution de l'application
FROM openjdk:17

# Définir le répertoire de travail
WORKDIR /app

# Définir les variables d'environnement directement dans le Dockerfile
ENV SPRING_APPLICATION_NAME=service-config
ENV SPRING_CLOUD_CONFIG_SERVER_GIT_URI=https://github.com/Raph16/DevOps-cloud-confic.git

# Copier le JAR construit depuis l'étape de construction
COPY --from=build /app/target/*.jar app.jar

# Exposer le port de l'application
EXPOSE 8080

# Exécuter l'application en tenant compte des variables d'environnement
ENTRYPOINT ["java", "-jar", "app.jar"]