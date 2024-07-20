
---

#  Setup Kubernetes On-Premise to Deploy Wisecow Application using Helm

## Overview
This guide provides step-by-step instructions for setting up Kubernetes on-premise and deploying the Wisecow application using Helm. We leverage Jenkins Pipeline to automate the entire process, ensuring a seamless deployment workflow.

## Prerequisites
Before you begin, ensure you have the following:

- **Kubernetes Cluster**: Ensure you have a Kubernetes cluster set up on-premise.
- **Helm**: Install Helm on your local machine and the Kubernetes cluster.
- **Jenkins**: Jenkins should be installed and configured on your system.
- **Docker**: Docker should be installed on your build and deployment servers.
- **Git**: Access to the Git repository where the Wisecow application and configuration files are stored.

## Setting Up Kubernetes
### Install Kubernetes
1. Follow the [Kubernetes installation guide](https://kubernetes.io/docs/setup/) to set up your cluster on-premise.
2. Ensure all nodes are correctly configured and the cluster is operational.

### Install Helm
1. Follow the [Helm installation guide](https://helm.sh/docs/intro/install/) to install Helm on your local machine.
2. Configure Helm with your Kubernetes cluster.

### Configure Kubernetes Credentials
1. Ensure that Kubernetes credentials are available for Jenkins to interact with the cluster.
2. Store these credentials securely in Jenkins using the kubeconfig file.

For more detailed information, check out this [Notion page](https://www.notion.so/All-Required-Things-which-needed-To-Provision-K8S-on-an-on-Premise-1eec48e905f44b53ad0df6d6ee57e3a0?pvs=4).

---
