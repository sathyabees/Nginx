#Setup
Minikube was installed on EC2 Amazon linux
1. Run a public EC2 Server with the following setup
--------------------------------------------------
Server = Amazon Linux 
Instance Type = t2.medium
Security Group = SSH, 0.0.0.0

2. Connect to Server
   ----------------
   
3. Install Docker
   ---------------
sudo yum install -y docker
sudo systemctl enable --now docker
sudo usermod -aG docker ec2-user
newgrp docker
sudo systemctl restart docker

4. Install kubectl
   ----------------

sudo systemctl status docker
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo mv kubectl /bin/kubectl

sudo su
sudo yum update -y
sudo systemctl status docker
kubectl version


5. Install Minikube
   ----------------

curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube
sudo mv minikube /usr/local/bin/minikube
minikube start
minikube status


6. Check Minikube Version
   ----------------------

minikube version

Deploying Nginx container on Kubernetes
---------------------------------------


1. Deploying Nginx Container

  kubectl run sample-nginx --image=nginx  --port=80
  kubectl get pods
  
  
2. Expose the deployment as service. This will create an ELB in front of those 2 containers and allow us to publicly access them:
   
 kubectl create -f nginx.yaml
 kubectl get deployments
 kubectl get services -o wide
