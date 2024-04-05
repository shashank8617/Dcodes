## DOCKER
# docker installtion

sudo yum update -y
sudo yum search docker
sudo yum info docker
sudo yum install -y docker
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service
docker --version

DOCKER FILE 

FROM amazonlinux
MAINTAINER shashank.karigowda@gmail.com
RUN yum update -y
RUN yum install wget -y
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.86/bin/apache-tomcat-9.0.86.tar.gz
RUN yum install tar -y
RUN yum install gzip -y
RUN tar -zxvf apache-tomcat-9.0.86.tar.gz
RUN yum install java-11* -y
RUN sh apache-tomcat-9.0.86/bin/startup.sh

//cmd to run the file docker build -t shashank8617/webapp Dockerfile/

DOCKER COMPOSE 

https://codeshare.io/alpha103

sudo yum update -y
sudo yum search docker
sudo yum info docker
sudo yum install -y docker
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service
docker --version
sudo yum install git -y
sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
