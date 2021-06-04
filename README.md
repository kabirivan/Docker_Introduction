# Docker_Introduction



# Create own images
docker build --tag apache-centos .
docker build -t apache-centos:apache-cmd .

# Run image
docker run -d apache-centos
docker run -d --name apache apache-centos 
docker run -d --name apache apache-centos:apache-cmd

# Run imagen in a specific port #port1 (computadora) : #port2 (contenedor)  
docker run -d --name apache -p 80:80 apache-centos:apache-cmd

# Delete Container
docker ps -a
docker rm -fv apache


# Notes

Ruta defecto Apache -> /var/www/html 