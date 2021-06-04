# Docker_Introduction



# Create own images
docker build --tag apache-centos .
docker build -t apache-centos:apache-cmd .

# Run image
docker run -d apache-centos
docker run -d --name apache apache-centos 

# Delete Container
docker ps -a
docker rm -fv apache