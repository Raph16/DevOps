# Projektaufgabe :

 Das Ziel dieses Projekts ist es, einen prototypischen Ansatz für eine vollständige DevOps
 Infrastruktur zu erarbeiten und zu demonstrieren, der auf die spezifischen Anforderungen
 unserer webbasierten Anwendung zugeschnitten ist. Dabei sollen alle Schritte der
 Softwareentwicklung und -bereitstellung, von der Code-Integration bis hin zur Auslieferung
 in einer produktionsnahen Umgebung, berücksichtigt werden.


### LAUNCH BACKEND
### Terminal öffnen und den unteren Befehl eingeben.
     docker compose up service-config service-registry 
     docker compose up account-service service-proxy

## LAUNCH FRONTEND
### Ein zweiter Terminal öffnen und den unteren Befehl eingeben, um den Front-end im lauf zu bringen
     docker compose up frontend


## VISIT APP
### Url in Browser eingeben
http://localhost:3001

## Admin Credentials
email : admin@localhost.cm
password : admin123