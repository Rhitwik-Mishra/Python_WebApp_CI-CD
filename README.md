# Python Web Application Deployment with Kubernetes and Jenkins

## Overview

This project demonstrates the automated deployment of a Python web application using Flask, Docker, Kubernetes, MySQL and Jenkins CI/CD. It also includes monitoring with Prometheus and Grafana for Jenkins servers and the Kubernetes cluster.

## Features

- **Flask Web Application**: A simple web app built with Flask.
- **MySQL Integration**: The application connects to a MySQL database.
- **Docker**: Containerizes the application for consistent deployment.
- **Kubernetes**: Manages the deployment, scaling, and operations of the application.
- **Jenkins CI/CD**: Automates the build, test, and deployment processes.
- **Prometheus**: Collects metrics from Jenkins and Kubernetes.
- **Grafana**: Visualizes metrics for real-time monitoring and alerting.

### Prerequisites

- Docker
- Kubernetes
- Jenkins
- Prometheus
- Grafana

### Setup

1. **Clone the repository**:
    ```sh
    git clone https://github.com/panditaashitta/Python_WebApp_CI-CD.git
    ```

2. **Configure Jenkins**:
    - Ensure Jenkins is set up with the necessary plugins for Docker and Kubernetes.
    - Add your Docker and Kubernetes credentials to Jenkins.
    - Create a new Jenkins pipeline job and point it to this repository.

### Jenkins CI/CD Pipeline

The Jenkins pipeline is defined in the `Jenkinsfile`. It performs the following steps:
1. **Checkout**: Retrieves the latest code from the repository.
2. **Build**: Builds the Docker image.
3. **Push**: Pushes the Docker image to Docker Hub.
4. **Deploy**: Applies the Kubernetes configurations to deploy the application.
5. **Rollout Deployment**: Restarts the deployment to apply the latest changes.

### Monitoring with Prometheus and Grafana

- **Prometheus**: Collects metrics from Jenkins and Kubernetes.
- **Grafana**: Visualizes the metrics for real-time monitoring and alerting.

## Usage

- Access the web application via the configured ingress URL.
- Monitor the application and infrastructure using Grafana dashboards.



"# Python_WebApp_CI-CD" "# Python_WebApp_CI-CD" 
