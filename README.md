# website-nginx

`website-nginx` is a web application containerized using Docker and managed with Ansible and Kubernetes. The project demonstrates horizontal auto-scaling to handle increased CPU loads efficiently, running in a cloud environment on AWS.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Kubernetes Scaling Demo](#kubernetes-scaling-demo)
- [Directory Structure](#directory-structure)

## Project Overview

`website-nginx` is designed to demonstrate a scalable web application deployment using modern DevOps tools. The application is containerized, automated, and managed in a Kubernetes cluster deployed on an AWS EC2 master node. It features auto-scaling capabilities triggered by CPU load.

## Features

- **Containerization**: Built using a Dockerfile for consistent application environments.
- **Automation**: Deployment automated with `ansible-playbook.yaml` and inventory files.
- **Auto-Scaling**: Configured Horizontal Pod Autoscaler to scale replicas from 1 to 5 when CPU usage exceeds 50%.
- **Load Testing**: Includes a `job.yaml` file to simulate high CPU loads for testing auto-scaling.
- **Service Integration**: Uses a Kubernetes service of type LoadBalancer to create AWS Elastic Load Balancer (ELB) and Target Groups automatically.

## Prerequisites

Before deploying the application, ensure the following:

### AWS Setup:
- AWS CLI configured with your credentials and default region.
- IAM permissions to create LoadBalancers, Target Groups, and manage EC2 instances.

### Kubernetes Setup:
- Kubernetes cluster configured to support the LoadBalancer service type with AWS as the cloud provider.

### Tools Installed:
- Docker for building and running the container.
- Ansible for automating deployment tasks.
- Kubernetes to manage deployments and scaling.

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com//website-nginx.git
   cd website-nginx

2. **Build Docker Image:**
   
   ```bash
   docker build -t website-nginx .

3. **Deploy the application using Ansible:**

    ```bash
   ansible-playbook ansible-playbook.yaml

4. **Apply Kubernetes resources:**

    ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   kubectl apply -f autoscale.yaml

## Usage

### Accessing the Application:
- The Kubernetes service is of type LoadBalancer.
- Run the following command to retrieve the LoadBalancer's external IP or DNS:

   ```bash
   kubectl get service
- Copy the EXTERNAL-IP or Hostname and access the application via your browser.

### Scaling and Monitoring:
- Monitor the Horizontal Pod Autoscaler (HPA):
   ```bash
   kubectl get hpa

- Check the current pods:
  ```bash
   kubectl get pods

### AWS Resources:
- The LoadBalancer service automatically provisions an AWS Elastic Load Balancer (ELB) and a Target Group. These resources handle routing traffic to the EC2 instances    
  hosting the application pods


## Kubernetes Scaling Demo

To test the auto-scaling feature:

1. **Apply the job.yaml file to create a pod that simulates high CPU load:**

   ```bash
   kubectl apply -f job.yaml

2. **Observe the Horizontal Pod Autoscaler (HPA):**

The number of replicas will scale from 1 to 5 as the CPU load increases.

3. **Monitor the scaling process using:**
 
   ```bash
   kubectl get hpa
   kubectl get pods

## Directory Structure

 website-nginx/
│
├── k8s/:                    Kubernetes deployment files
│   ├── deployment.yaml      Kubernetes deployment definition
│   ├── service.yaml         Kubernetes LoadBalancer service definition
│   ├── autoscale.yaml       Kubernetes Horizontal Pod Autoscaler configuration
│   └── job.yaml             Kubernetes job for load testing
│
├── sample-website/:         Contains the source code of the application
│   └── ...                  Application files (HTML, CSS, JS, etc.)
│
├── Dockerfile               Docker configuration file
├── ansible-playbook.yaml    Ansible automation script (with job cleanup)
├── inventory.ini            Ansible inventory file
└── README.md                Project documentation

   
