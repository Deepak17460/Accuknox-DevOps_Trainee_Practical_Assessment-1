Setup Kubernetes on Premise to Deploy Wisecow Application using Helm
Overview
This guide provides step-by-step instructions for setting up Kubernetes on-premise and deploying the Wisecow application using Helm. We leverage Jenkins Pipeline to automate the entire process, ensuring a seamless deployment workflow.

Prerequisites
Kubernetes Cluster: Ensure you have a Kubernetes cluster set up on-premise.
Helm: Install Helm on your local machine and the Kubernetes cluster.
Jenkins: Jenkins should be installed and configured on your system.
Docker: Docker should be installed on your build and deployment servers.
Git: Access to the Git repository where the Wisecow application and configuration files are stored.
Setting Up Kubernetes
Install Kubernetes:

Follow the Kubernetes installation guide to set up your cluster on-premise.
Ensure all nodes are correctly configured and the cluster is operational.
Install Helm:

Follow the Helm installation guide to install Helm on your local machine and configure it with your Kubernetes cluster.
Configure Kubernetes Credentials:

Ensure that Kubernetes credentials are available for Jenkins to interact with the cluster. Store these credentials securely in Jenkins using the kubeconfig file.
Jenkins Pipeline for Kubernetes Deployment
The Jenkins Pipeline automates the process of building Docker images, pushing them to a Docker registry, and deploying them to Kubernetes using Helm. The pipeline script is configured as follows:
