# Course-Docker
Getting Started
Follow these instructions to get a copy of the project up and running on your local machine.

## Prerequisites

Make sure you have the following installed:
Docker

## Installation
### Clone the repository:
git clone https://github.com/aaabaza761/website-nginx.git
cd nginx-docker-webpage
## RUNNING
Build and run the Docker containers: docker-compose up --build
Open your browser and navigate to http://localhost:8080 to see the web page.
OR

## Docker Hub Image
You can also pull the Docker image directly from Docker Hub:
docker pull ahmed377/new-web:latest
docker run -p 4000:80 ahmed377/nginx-webpage:latest
## Kubernetes Deployment

This section describes how to deploy the web application using Kubernetes.

### Prerequisites

Make sure you have the following installed:

- Kubernetes cluster (e.g., Minikube, GKE, EKS, AKS)
- kubectl

### Deployment Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/aaabaza761/website-nginx.git
   cd website-nginx/k8s
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   kubectl apply -f autoscale.yaml

