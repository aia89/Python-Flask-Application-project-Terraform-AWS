# Python Flask Application #
Flask is a lightweight web framework for Python, ideal for developing simple web applications. 

In this project:

* app.py:

  Defines a basic web application with a single route (/) returning "Hello, World!".
  
  Can be extended to include more routes and logic as needed.
* requirements.txt:

  * Lists dependencies required for the application:
    - flask: Core framework.
    - gunicorn: A production-grade WSGI HTTP server.
    
This simple setup serves as a template for any web application that needs to be hosted and scaled on Kubernetes.
#

# Dockerization
Docker allows packaging the application into a portable container that includes the application code, runtime, and dependencies.

* Dockerfile:
- Builds a lightweight image using python:3.10-slim.
- Installs required dependencies.
- Runs the application using Gunicorn, a production-grade WSGI server.


Once built, the Docker image is pushed to a container registry (e.g., Docker Hub), ready to be deployed on Kubernetes.
#

# Helm for Kubernetes Deployment
Helm simplifies the deployment of Kubernetes applications by templating the YAML files for Kubernetes resources.

## Helm Chart:
- Manages Kubernetes resources like Deployments, Services, and Ingress.
- The values.yaml file allows customizing configurations, such as image details and replicas.

## Key resources:

- Deployment: Ensures the Flask app runs with 3 replicas for high availability.
- Service: Exposes the application within the cluster.
- Ingress: Enables external access to the app via flask-app.example.com.


# Terraform for AWS Infrastructure
Terraform provisions the cloud infrastructure required to run the Kubernetes cluster:

## VPC:
- Creates a virtual network with subnets for public and private access.

## EKS Cluster:
- Deploys an Elastic Kubernetes Service (EKS) cluster.
- Configures node groups (EC2 instances) for running Kubernetes workloads.

This setup provides a secure and scalable infrastructure for hosting the Flask application.



# CI/CD with GitHub Actions
Automates the build, test, and deployment process:

## Pipeline Workflow:
- Build: Installs dependencies and ensures the Flask app is ready.
- Dockerize: Builds and pushes the Docker image to a container registry.
- Deploy: Uses Helm to deploy or update the application in the Kubernetes cluster.

This ensures every change in the codebase is automatically tested and deployed.


