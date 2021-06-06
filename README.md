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
### Run

docker run --help|less
docker run -d jenkins
docker run -d -p 3000:8080 jenkins/jenkins

### Remove
docker rm -f name 

### Rename
docker rename romantic_ptolemy jenkins

### Stop
docker stop container ID

### Start
docker start container ID | name
docker restart container ID | name

### Container Inside

docker exec -ti bd80f19b15ab bash
whoami
hostname
docker exec -u root -ti bd80f19b15ab bash


### Jenkins
cat /var/jenkins_home/secrets/initialAdminPassword

### Environment Variable

### Remove All Containers
docker ps -q | xargs docker rm -f
docker rm -fv $(docker ps -aq)


## Create MySQL Container
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
docker run --name my-db1 -e MYSQL_ROOT_PASSWORD=12345 -d mysql:5.7
docker logs -f my-db1      

docker run --name my-db2 -e MYSQL_ROOT_PASSWORD=12345 -p 3333:3306 -e MYSQL_DATABASE=docker -e MYSQL_USER=docker -e MYSQL_PASSWORD=1234  -d mysql:5.7

## Map ports
docker inspect my-db1
"IPAddress": "172.17.0.2"


## Create Mongo Container
docker run -d --name my-mongo -p 27017:27017 mongo:latest
docker stats my-mongo