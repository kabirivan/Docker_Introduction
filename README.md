# Docker_Introduction



# Create own images
docker build --tag apache-centos .
docker build -t apache-centos:apache-cmd .

docker build -t test -f my-dockerfile .

# Run image
docker run -d apache-centos
docker run -d --name apache apache-centos 
docker run -d --name apache apache-centos:apache-cmd

# Run imagen in a specific port #port1 (computadora) : #port2 (contenedor)  
docker run -d --name apache -p 80:80 apache-centos:apache-cmd

# Delete Container
docker ps -a
docker rm -fv apache

# View datasource

docker ps --no-trunc


# Generate ssl to apache

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout docker.key -out docker.crt

# Delete image
docker rmi apache-centos  

# Images Dangling
docker images -f dangling=true
docker images -f dangling=true -q | xargs docker rmi


# Notes

Ruta defecto Apache -> /var/www/html 
revisar tamano archivos -> du -sh *   du -shc *


# Containers

docker run --help|less
docker run -d jenkins
docker run -d -p 3000:8080 jenkins/jenkins
docker rm -f name 



