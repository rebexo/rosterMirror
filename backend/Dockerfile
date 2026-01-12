## Build Stage: Image nutzen, das Maven schon hat (viel stabiler)
#FROM maven:3.9-eclipse-temurin-21 AS build
#WORKDIR /app
#
## Nur die pom.xml kopieren, damit Docker die Dependencies cachen kann
#COPY pom.xml ./
#
## Dependencies laden (jetzt mit dem vorinstallierten 'mvn' Befehl)
#RUN mvn dependency:go-offline
#
## Quellcode holen und bauen
#COPY src ./src
#RUN mvn clean package -DskipTests
#
## Run Stage
#FROM eclipse-temurin:21-jre-alpine
#WORKDIR /app
#COPY --from=build /app/target/*.jar app.jar
#EXPOSE 8080
#ENTRYPOINT ["java", "-jar", "app.jar"]

#----------------------- wenn maven-build schon auf vm gelaufen ist------------------
# Wir brauchen kein Maven mehr, wir haben ja schon gebaut
FROM eclipse-temurin:21-jre-alpine

WORKDIR /app

# Wir kopieren die JAR, die dank deines "BUILD SUCCESS" auf dem Host liegt
COPY target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]