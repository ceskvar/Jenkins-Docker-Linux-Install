# Jenkins-Docker-Linux-Install
## Prerrequisites:
* Java 8 runtime
* Docker engine

## Instructions
1. clone the Dockerfile
```
wget https://github.com/ceskvar/Jenkins-Docker-Linux-Install.git
```
2. build the docker image
```
sudo docker build -t myjenkins-blueocean:1.1 .
```
3. execute the container
```
sudo docker run --name jenkins-blueocean --rm --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  myjenkins-blueocean:1.1
```
4. get a password (change id_contenedor for your own)
```
sudo docker exec id_contenedor cat var/Jenkins_home/secrets/initialAdminPassword
```
