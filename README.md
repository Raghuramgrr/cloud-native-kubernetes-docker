# cloud-native-kubernetes-docker


## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Kubernetes](https://kubernetes.io/docs/setup/) (via kubeadm, kind, or minikube)
- [Helm](https://helm.sh/docs/intro/install/)

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/raghuramgrr/cloud-native-kubernetes-docker.git
   cd cloud-native-kubernetes-docker
    ```

2. Navigate to the Dockerfiles directory and build the Docker image
```bash
    cd dockerfiles
    docker build -t myapp .
```

3. Set up your Kubernetes cluster using the provided script:
 ```bash
    cd k8s-cluster-setup
    bash setup-cluster.sh
```
4.Apply the Kubernetes manifests:
```bash
    kubectl apply -f ../microservices/k8s-manifests/deployments/myapp-deployment.yaml
    kubectl apply -f ../microservices/k8s-manifests/services/myapp-service.yaml
```

5.(Optional) Install the Helm chart:
```bash
    cd ../helm-charts/myapp
    helm install myapp .
``` 

Usage
Once deployed, you can access your application through the service created in Kubernetes. For example, if you're using ClusterIP, you'll need to port-forward to access it locally:
```bash
    kubectl port-forward service/myapp-service 8080:80
``` 
Now, you can access your application at http://localhost:8080.

