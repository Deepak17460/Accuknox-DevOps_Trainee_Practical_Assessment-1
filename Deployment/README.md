
---

# Deploy Wisecow Application to Kubernetes using Helm

## Overview
This guide provides detailed instructions for deploying the Wisecow application to a Kubernetes cluster using Helm. By leveraging Helm, we simplify the deployment process and ensure a consistent and repeatable setup.

## Prerequisites
Before you begin, ensure you have the following:

- **Kubernetes Cluster**: A Kubernetes cluster set up on-premise or in the cloud.
- **Helm**: Installed on your local machine and configured with your Kubernetes cluster.
- **Docker**: Installed on your build and deployment servers.
- **Git**: Access to the Git repository where the Wisecow application and configuration files are stored.

## Setting Up Kubernetes and Helm
### Install Kubernetes
1. Follow the [Kubernetes installation guide](https://kubernetes.io/docs/setup/) to set up your cluster.
2. Ensure all nodes are correctly configured and the cluster is operational.

### Install Helm
1. Follow the [Helm installation guide](https://helm.sh/docs/intro/install/) to install Helm on your local machine.
2. Configure Helm with your Kubernetes cluster.

### Configure Kubernetes Credentials
1. Ensure that Kubernetes credentials are available for Jenkins to interact with the cluster.
2. Store these credentials securely in Jenkins using the kubeconfig file.

For more detailed information, check out this [Notion page](https://www.notion.so/All-Required-Things-which-needed-To-Provision-K8S-on-an-on-Premise-1eec48e905f44b53ad0df6d6ee57e3a0?pvs=4).

## Deploying Wisecow Application using Helm
### Step 1: Clone the Repository
Clone the Git repository containing the Wisecow application and Helm chart:
```bash
git clone https://github.com/Deepak17460/Accuknox-DevOps_Trainee_Practical_Assessment-.git
cd Accuknox-DevOps_Trainee_Practical_Assessment-
```

### Step 2: Build Docker Image
Build the Docker image for the Wisecow application:
```bash
docker build -t dpcode72/wisecow:1.0 .
docker push dpcode72/wisecow:1.0
```

### Step 3: Deploy with Helm
Deploy the Wisecow application to your Kubernetes cluster using Helm:
```bash
helm upgrade --install wisecow ./helm-chart --set image.repository=dpcode72/wisecow --set image.tag=1.0
```

### Step 4: Verify Deployment
Check the status of your deployment:
```bash
kubectl get pods
kubectl get services
```

## Conclusion
You have successfully deployed the Wisecow application to your Kubernetes cluster using Helm. For any issues or further assistance, feel free to reach out.

---

Feel free to copy and paste this into your README. If you need any more adjustments, just let me know! 😊

Source: Conversation with 
(1) Getting Started with Helm: Simplifying Kubernetes Deployments with Best .... https://www.kubernet.dev/getting-started-with-helm-simplifying-kubernetes-deployments-with-best-practices-and-lessons/.
(2) 13 Best Practices for using Helm - Coder Society. https://codersociety.com/blog/articles/helm-best-practices.
(3) Using Helm to Deploy Kubernetes to Multiple Environments - Codefresh. https://codefresh.io/blog/helm-deployment-environments/.
(4) andredesousa/kubernetes-best-practices - GitHub. https://github.com/andredesousa/kubernetes-best-practices.
(5) Kafka on Kubernetes: Best Practices for Deployment and Management. https://reintech.io/blog/kafka-on-kubernetes-deployment-and-management.
(6) undefined. https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3.
(7) undefined. https://charts.bitnami.com/bitnami.
(8) undefined. https://hub.helm.sh/charts/bitnami/mysql.
