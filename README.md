
---

# Deploy Wisecow Application to Kubernetes using Helm

![image](https://github.com/user-attachments/assets/d04e2d4b-1efb-44ae-bc6d-bd4deb957965)

## Overview
This project demonstrates the deployment of the Wisecow application to a Kubernetes cluster using Helm. The deployment process is automated using Jenkins for Continuous Integration (CI) and Continuous Deployment (CD). This ensures a seamless and efficient workflow from code commit to deployment. Additionally, TLS is used for secure communication.

## Prerequisites
Before you begin, ensure you have the following:

- **Kubernetes Cluster**: A Kubernetes cluster set up on-premise or in the cloud.
- **Helm**: Installed on your local machine and configured with your Kubernetes cluster.
- **Jenkins**: Installed and configured for CI/CD.
- **Docker**: Installed on your build and deployment servers.
- **Git**: Access to the Git repository where the Wisecow application and configuration files are stored.

## Docker Image
The Docker image for the Wisecow application is available at:
```bash
docker pull dpcode72/wisecow:1.0
```
Docker Image run
```bash
docker run -d -p 4499:4499 --name wisecow dpcode72/wisecow:1.0
```
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

## Jenkins Pipeline for CI/CD
The Jenkins Pipeline automates the process of building Docker images, pushing them to a Docker registry, and deploying them to Kubernetes using Helm. Below is an example of the Jenkins Pipeline script:

```groovy
pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS_ID = 'docker-credentials'
        KUBECONFIG_CREDENTIALS_ID = 'kubeconfig'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('wisecow-app')
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', DOCKER_CREDENTIALS_ID) {
                        docker.image('wisecow-app').push('1.0')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    withKubeConfig([credentialsId: KUBECONFIG_CREDENTIALS_ID]) {
                        sh 'helm upgrade --install wisecow ./helm-chart --set image.repository=dpcode72/wisecow --set image.tag=1.0'
                    }
                }
            }
        }
    }
}
```

## TLS for Secure Communication
To ensure secure communication, TLS has been configured for all interactions between Jenkins, Docker, and Kubernetes. This helps protect data integrity and privacy.

## Verifying Deployment
After deployment, verify the status of your application:
```bash
kubectl get pods
kubectl get services
```

## Conclusion
You have successfully deployed the Wisecow application to your Kubernetes cluster using Helm and Jenkins for CI/CD, with TLS ensuring secure communication. For any issues or further assistance, feel free to reach out.

---
