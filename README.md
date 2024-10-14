# website-nginx
Kubernetes deployment for website-nginx on AWS with Docker support, featuring HPA, ELB, Target Groups, and EFS integration for scalable web hosting.
Table of Contents

## Features
## Prerequisites
## Installation
## Usage

### Local Development with Docker
### Using Docker Hub Image
### Kubernetes Deployment on AWS


## Architecture
## Benefits

## Features

  Kubernetes Deployment for website-nginx application
  Horizontal Pod Autoscaler (HPA) for dynamic resource management
  AWS Integration:

      Elastic File System (EFS) for persistent storage
      Elastic Load Balancer (ELB) for traffic distribution
      Target Groups for request routing


Docker support for local development and testing
Pre-built Docker image available on Docker Hub

## Prerequisites

  Docker
  Git (for cloning the repository)
  AWS account (for Kubernetes deployment)

## Installation

  Clone the repository:
  Copygit clone https://github.com/aaabaza761/website-nginx.git
  cd website-nginx


## Usage
    Local Development with Docker

    Build and run using Docker Compose:
      docker-compose up --build

      Access the web page at http://localhost:8080

   Using Docker Hub Image

    Pull and run the pre-built Docker image:
      docker pull ahmed377/new-web:latest
      docker run -p 4000:80 ahmed377/nginx-webpage:latest

Access the web page at http://localhost:4000

## Kubernetes Deployment on AWS
For Kubernetes deployment, use the provided manifests:

  deployment.yaml: Kubernetes Deployment configuration
  service.yaml: LoadBalancer Service configuration
  hpa.yaml: Horizontal Pod Autoscaler configuration
  storage-class.yaml: EFS StorageClass configuration
  pvc.yaml: PersistentVolumeClaim configuration

Apply these manifests to your Kubernetes cluster on AWS.
Architecture

## Kubernetes: Orchestrates containerized application deployment
## Docker: Containerizes the nginx web server
## AWS EFS: Provides persistent storage for the application
## AWS ELB: Distributes incoming traffic across multiple targets
## AWS Target Groups: Routes requests to registered Kubernetes pods

### Benefits

  ## High Availability: Ensured through load balancing
  ## Scalability: Automatic scaling with HPA and ELB
  ## Efficiency: Optimized resource utilization
  ## Persistence: Data persistence across pod lifecycles with EFS
  ## Cloud-Native: Leverages AWS services for enhanced functionality
  ## Local Development: Easy setup for testing using Docker
