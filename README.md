# **Guide de Déploiement Kubernetes — Example Voting App**

Ce guide a pour but de vous accompagner dans le déploiement de l'application example-voting-app sur un cluster Kubernetes local (via Minikube), de valider son bon fonctionnement, et de produire une représentation claire de son architecture.

# Architecture
![Diagramme_sans_nom drawio_1](https://github.com/user-attachments/assets/4cb79ea7-8788-4b73-88d7-eaaf2146cf96)

# **Prérequis Techniques**

Avant de commencer, assurez-vous de disposer des éléments suivants :

Une machine sous Ubuntu 20.04 ou 24.04 (ou équivalent Linux)

Logiciels installés :

Docker

Minikube

kubectl

git

# **Mise à jour du système (recommandée)**

sudo apt update && sudo apt upgrade -y

**Installation des outils nécessaires**
sudo apt install -y curl git

# Installer Docker
sudo apt install docker.io -y

sudo usermod -aG docker $USER

newgrp docker

# Installer kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl && sudo mv kubectl /usr/local/bin/

# Installer Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube


# Cloner le dépôt GitHub
git clone https://github.com/dockersamples/example-voting-app

cd example-voting-app

# Se placer dans le dossier contenant les fichiers YAML Kubernetes
cd k8s-specifications

# Démarrer Minikube avec le driver Docker
minikube start --driver=docker

# Déployer les objets Kubernetes
kubectl apply -f .

# Vérifier l’état du cluster
kubectl get pods

![image](https://github.com/user-attachments/assets/11d73a14-b20b-4e2a-ab66-0e9ad7c16db9)

kubectl get svc

![image](https://github.com/user-attachments/assets/69225740-254b-4fb4-ba11-e154a7fb196c)


# Accéder aux interfaces web
minikube service vote

![image](https://github.com/user-attachments/assets/7fcc1e29-9328-4387-a15f-aec66acbe2e6)

minikube service result

![image](https://github.com/user-attachments/assets/fac63766-ca61-4bad-b0e2-89c0e0883508)


vote : http://<minikube_ip>:31000
![image](https://github.com/user-attachments/assets/d2e5bd9c-d179-47cd-a528-160318d0d106)

result : http://<minikube_ip>:31001
![image](https://github.com/user-attachments/assets/f6902bc1-38b1-43eb-8abb-09bf9bd459eb)


