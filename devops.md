# TERAAFORM
```bash
provider "aws" {
  region = "ap-south-1"  
  access_key = "AKIA4T7L7RY4V56"
  secret_key = "rJmMPEAVmDStX/njCR1Z/e4zP"
}

resource "aws_instance" "example-1" {
  ami           = "ami-018733779cdf8"
  instance_type = "t2.micro"
  key_name = "mumbailinux"
  aws_security
  count = "1"
  tags = {
    Name = "ExampleInstance" 
  }
}
resource "aws_security_groups" "example-1" {
  tags = {
    Name = "ExampleInstance" 
  }
}
```




# DOCKER
```bash
sudo yum update -y
sudo yum search docker
sudo yum info docker
sudo yum install -y docker
sudo systemctl enable docker.service
sudo systemctl start docker.service
sudo systemctl status docker.service
docker --version
```
# DOCKER FILE 
```bash
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
```
//cmd to run the file docker build -t shashank8617/webapp Dockerfile/
https://codeshare.io/alpha103
# DOCKER COMPOSE 
```bash
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
```
22
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
# .yml (script)
```bash
version: '3'
services:
  web:
    image: nginx
    ports:
      - '4000:80'
  db:
    image: redis


YML



version:'3'
services:
  web:
    images:nginx
  ports:
    -4000:80
  db:
    image:redis
```
# JENKINS
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-17-openjdk
sudo yum install jenkins
sudo systemctl daemon-reload
```
# connection to vpc
```bash
  secret_key = "eGn4QluGGhtYYuuODvgXoh8V"
}

resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "example_public" {
  vpc_id     = aws_vpc.example.id
  cidr_block = "10.0.1.0/24"
}

resource "aws_security_group" "example_sg" {
  vpc_id = aws_vpc.provider "aws" {
  region = "ap-south-1"
  access_key = "AKIA305JEL4"
  secret_key = "eGn4QluG7YYuuODvgXoh8V"
}

resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "example_public" {
  vpc_id     = aws_vpc.subnet-0ff77d87097016ced
  cidr_block = "10.0.1.0/24"
}

resource "aws_security_group" "sg" {
  vpc_id = aws_vpc.vpc-0c0df968e4dd60532

  ingress {
    from_port   = 80
    to_port     = 80
```
# Jenkins Pipeline
```bash

pipeline {
    agent any
    
    stages {
        stage('Test') {
            steps {
                script {
                    def output = docker.image("hello-world:${env.BUILD_ID}").inside {
                        sh 'docker exec $(docker ps -q) python hello_world.py'
                    }
                    echo output
                    if (!output.contains("Hello, World!")) {
                        error "Test failed: 'Hello, World!' not found in output."
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                docker.image("hello-world:${env.BUILD_ID}").remove()
            }
        }
    }
}
```
























provider "aws" {
  region     = "ap-south-1"
  access_key = "AKIARPORSUG"
  secret_key = "CQ3scxpVTkB9Slgny"
}

resource "aws_vpc" "example" {
  cidr_block = "10.0.0.0/16"
}

resource "aws_subnet" "example_public" {
  vpc_id     = "vpc-0c0df968e4dd60532"
  cidr_block = "10.0.0.0/16"
}

resource "aws_security_group" "example_sg" {
  vpc_id = "vpc-0c0df0532"

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

resource "aws_instance" "example-1" {
  ami             = "ami-0187337106779cdf8"
  instance_type   = "t2.micro"
  key_name        = "shashank"
  count           = 1
  subnet_id       = "subnet-0ff6ced"
  security_groups = [aws_security_group.example_sg.id]

 user_data = <<-EOF
              #!/bin/bash
              sudo yum install -y httpd
              sudo systemctl start httpd
              sudo systemctl enable httpd
              EOF


  tags = {
    Name = "ExampleInstance"
  }
}
           

                                                                                                                                            1,1           Top


If docker is present don't install docker or else install docker 
Docker install










Jenkins deployment code for USER.XML file

<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<user username="admin" password="admin" roles="manager-gui, manager-script, manager-jmx, manager-status"/>


//////////////////////////////KUBERNETES CLUSTER SCRIPT////////////////////

# disable swap
sudo swapoff -a

# Create the .conf file to load the modules at bootup
cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
overlay
br_netfilter
EOF

sudo modprobe overlay
sudo modprobe br_netfilter

# sysctl params required by setup, params persist across reboots
cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables  = 1
net.bridge.bridge-nf-call-ip6tables = 1
net.ipv4.ip_forward                 = 1
EOF

# Apply sysctl params without reboot
sudo sysctl --system

## Install CRIO Runtime
sudo apt-get update -y
sudo apt-get install -y software-properties-common curl apt-transport-https ca-certificates gpg

sudo curl -fsSL https://pkgs.k8s.io/addons:/cri-o:/prerelease:/main/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/cri-o-apt-keyring.gpg
echo "deb [signed-by=/etc/apt/keyrings/cri-o-apt-keyring.gpg] https://pkgs.k8s.io/addons:/cri-o:/prerelease:/main/deb/ /" | sudo tee /etc/apt/sources.list.d/cri-o.list

sudo apt-get update -y
sudo apt-get install -y cri-o

sudo systemctl daemon-reload
sudo systemctl enable crio --now
sudo systemctl start crio.service

echo "CRI runtime installed successfully"

# Add Kubernetes APT repository and install required packages
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update -y
sudo apt-get install -y kubelet="1.29.0-*" kubectl="1.29.0-*" kubeadm="1.29.0-*"
sudo apt-get update -y
sudo apt-get install -y jq

sudo systemctl enable --now kubelet
sudo systemctl start kubelet

/////////////////////////KUBERNETES CLUSTER SCRIPT///////////////////////////


-----///////////////master//////////////////////////////////////////////-------------------------

mkdir -p $HOME/.kube



only in the master node:
when you complete all above procedure:

kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.26.0/manifests/calico.yaml

-----///////////////master//////////////////////////////////////////////-------------------------







Worker node history

    1  vi kube.sh
    2  sh kube.sh cat kube.sh 
    3  kubelet --version
    4  sudo kubeadm reset pre-flight checks
    5  sudo kubeadm join 172.31.46.128:6443 --token c0lqy3.1tnql1919grjez5r         --discovery-token-ca-cert-hash sha256:ba0dfed9eae9d61b00466e1ae0802 --v=5
    6  docker --version
    7  kubelet --version
    8  history

Master node history

    1  vi kube.sh
    2  sh kube.sh cat kube.sh 
    3  kubelet --version
    4  sudo kubeadm config images pull
    5  sudo kubeadm init
    6  mkdir -p $HOME/.kube
    7  kubectl get nodes
    8  kubectl get pods
    9  vi pod.yml
   10  kubectl apply -f pod.yml 
   11  kubectl get pods
   12  kubectl delete -f pod.yml 
   13  kubectl get pods
   14  kubectl get nodes
   15  kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.26.0/manifests/calico.yaml
   16  kubectl get pods
   17  kubectl get nodes
   18  cat pod.yml 
   19  ls
   20  kubectl apply -f pod.yml 
   21  kubectl get pods
   22  kubectl get pods -o wide
   23  kubectl describe pod jspiders
   24  kubectl get pods
   25  kubectl logs -f jspiders
   26  kubectl logs pod jspiders
   27  kubectl logs -f jspiders
   28  kubectl delete -f pod.yml 
   29  kubectl get pods
   30  vi pod.yml 
   31  cat pod.yml 
   32  kubectl apply -f pod.yml 
   33  kubectl get pods
   34  kubectl get pods -o wide
   35  kubectl describe pod jspiders
   36  kubectl log -f jspiders -c c1
   37  kubectl logs -f jspiders -c c1
   38  kubectl delete -f pod.yml 
   39  history



	mkdir -p $HOME/.kube
	sudo cp -i /etc/kubernetes/admin.conf $HOME/ .kube/config
	sudo chown $(id -u):$(id -g) $HOME/ .kube/config

	


kind: Pod
apiVersion: v1
metadata:
  name: jspiders
spec:
  containers:
    - name: sample1
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo Hi everyone; sleep 5; done"]
  restartPolicy: Never      #Default to Always


kind: Pod
apiVersion: v1
metadata:
  name: jspiders
spec:
  containers:
    - name: sample1
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo Hi everyone; sleep 5; done"]
    - name: sample2
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo Hi everyone; sleep 5; done"]
  restartPolicy: Never      #Default to Always




apiVersion: v1
Kind: Pod
metadata:  gtegtsjuy		y	t	u	g	y	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	gt	





------*************SCRIPTS**************-------------
TASKS MANIFESTS
----//for 1 pod with 1 container with the image of ubuntu//---

kind: pod
apiVersion: v1
metadata:
  name: jspiders
spec:
  containers:
    - name: jspiders
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo hi everyone; sleep 5; done"]

----//create one pod with 2 containers//-----
apiVersion: v1
kind: Pod
metadata:
  name: flipkart
spec:
  containers:
    - name: jspiders
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo hi everyone; sleep 5; done"]
    - name: qsp
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo hi everyone; sleep 5; done"]
  restartPolicy: Never     #Defaults to always

----//create 1 pod with image nginx and assign port no 80//-----
apiVersion: v1
kind: Pod
metadata:
  name: flipkart
spec:
  containers:
    - name: login
      image: nginx
      ports:
        - containerPort: 80

----//create a task with labels(used to find the individual containers by label name)//----

apiVersion: v1
kind: Pod
metadata:
  name: jspiders
  labels:
    department: DevOps
    batch: jddw3
spec: 
  containers:
    - name: demo
      image: ubuntu
      command: ["/bin/bash", "-c", "while true; do echo hi everyone; sleep 5; done"]

------//REPLICATION CONTAINER//-----


apiversion: v1
kind: ReplicationController
metadata:
  name: flipkart
spec:
  replicas: 2
  selector:
    app: nginx
  template:
    metadata:
      name: signup
      labels:
        app: nginx
    spec:
      containers:
        - name: signupemail
          image: nginx
          ports:
          - containersPort: 80

------//REPLICA SET\\-------


apiVersion: v1
kind: ReplicaSet
metadata:
  name: jsp
spec:
  replicas: 2
  selector:
    matchExpressions:
    - {key: myname, operator: In, values: [qspider, jspider, pyspider]}
    - {key: env, operator: NotIn, values: [skillnary]}
  template:
    metadata:
      name: sak
      labels:
        myname: qspider
    spec:
      containers:
        - name: abc
          image: ubuntu
          command: ["/bin/bash", "-c", "while true; do echo hello world; sleep 3; done"]




------*************SCRIPTS**************-------------





confg
Webapp
Inf

**/*/.war


https://codeshare.io/alpha103
