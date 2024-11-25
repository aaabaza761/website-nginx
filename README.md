# website-nginx
website-nginx is a web application containerized using Docker and managed with Ansible and Kubernetes. The project demonstrates horizontal auto-scaling to handle increased CPU loads efficiently, running in a cloud environment on AWS.

# Table of Contents  

- Project Overview  
- Features  
- Prerequisites  
- Getting Started  
- Usage  
- Kubernetes Scaling Demo  
- Directory Structure  


# Project Overview
website-nginx is designed to demonstrate a scalable web application deployment using modern DevOps tools. The application is containerized, automated, and managed in a Kubernetes cluster deployed on an AWS EC2 master node. It features auto-scaling capabilities triggered by CPU load.

# features
Containerization: Built using a Dockerfile for consistent application environments.
Automation: Deployment automated with ansible-playbook.yaml and inventory files.
Auto-Scaling: Configured Horizontal Pod Autoscaler to scale replicas from 1 to 5 when CPU usage exceeds 50%.
Load Testing: Includes a job.yaml file to simulate high CPU loads for testing auto-scaling.
Service Integration: Uses a Kubernetes service of type LoadBalancer to create AWS Elastic Load Balancer (ELB) and Target Groups automatically.
Prerequisites
Before deploying the application, ensure the following:

## AWS Setup:

AWS CLI configured with your credentials and default region.
IAM permissions to create LoadBalancers, Target Groups, and manage EC2 instances.

## Kubernetes Setup:

 Kubernetes cluster configured to support the LoadBalancer service type with AWS as the cloud provider.

## Tools Installed:

Docker for building and running the container.
Ansible for automating deployment tasks.
Kubernetes to manage deployments and scaling.

# Getting Started

## Clone the repository:
git clone https://github.com/<your-username>/website-nginx.git  
cd website-nginx  

## Build the Docker image:
docker build -t website-nginx .  


## Deploy the application using Ansible:
## Update the inventory file with your EC2 instance details.
## Run the playbook:
ansible-playbook ansible-playbook.yaml  


## Apply Kubernetes resources:
kubectl apply -f deployment.yaml  
kubectl apply -f service.yaml  
kubectl apply -f autoscale.yaml  

# Usage

## Accessing the Application:
## The Kubernetes service is of type LoadBalancer.

## Run the following command to retrieve the LoadBalancer's external IP or DNS:
kubectl get service  
Copy the EXTERNAL-IP or Hostname and access the application via your browser.

## Scaling and Monitoring:

### Monitor the Horizontal Pod Autoscaler (HPA):
kubectl get hpa  

### Check the current pods:
kubectl get pods  

## AWS Resources:

The LoadBalancer service automatically provisions an AWS Elastic Load Balancer (ELB) and a Target Group. These resources handle routing traffic to the EC2 instances hosting the application pods.
### Kubernetes Scaling Demo
### To test the auto-scaling feature:

## Apply the job.yaml file to create a pod that simulates high CPU load:
kubectl apply -f job.yaml  

### Observe the Horizontal Pod Autoscaler (HPA):
### The number of replicas will scale from 1 to 5 as the CPU load increases.
### Monitor the scaling process using:
kubectl get hpa  
kubectl get pods  


Certainly! Here's the updated Directory Structure section in Markdown format, suitable for your README.md file:


## Directory Structure  

website-nginx/
├── sample-website/ # Contains the source code of the application
│ └── ... # Application files (HTML, CSS, JS, etc.)
├── k8s/ # Kubernetes deployment files
│ ├── deployment.yaml # Kubernetes deployment definition
│ ├── service.yaml # Kubernetes LoadBalancer service definition
│ ├── autoscale.yaml # Kubernetes Horizontal Pod Autoscaler configuration
│ └── job.yaml # Kubernetes job for load testing
├── Dockerfile # Docker configuration file
├── inventory.ini # Ansible inventory file
└── ansible-playbook.yaml # Ansible automation script







