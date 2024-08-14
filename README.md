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
