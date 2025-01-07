# Deploy MERN App To K8s (Minikube)

This project demonstrates deploying a full-stack application on Kubernetes using Helm. It consists of MongoDB, Mongo Express, a Note API server, and a Note application. The chart includes configurations for deployments, services, secrets, and a config map.

## Project Structure
.
├── README.md
└── kubernetes-demo
    ├── Chart.yaml
    ├── charts
    ├── templates
    │   ├── config
    │   │   └── app-config.yaml
    │   ├── deployments
    │   │   ├── mongo-express-deployment.yaml
    │   │   ├── mongodb-deployment.yaml
    │   │   ├── note-deployment.yaml
    │   │   └── note-server-deployment.yaml
    │   ├── secrets
    │   │   └── app-secret.yaml
    │   └── services
    │       ├── mongo-express-service.yaml
    │       ├── mongodb-service.yaml
    │       ├── note-server-service.yaml
    │       └── note-service.yaml
    └── values.yaml


## Components

1. **MongoDB**: A NoSQL database for storing application data.
2. **Mongo Express**: A web-based MongoDB administrative interface.
3. **Note Server**: A backend API for managing notes.
4. **Note Application**: A frontend application for interacting with the Note Server.

### Configuration Files

- **`values.yaml`**: Contains configuration values for the Helm chart.
- **Templates**:
  - **Deployments**:
    - `mongodb-deployment.yaml`: Deploys MongoDB.
    - `mongo-express-deployment.yaml`: Deploys Mongo Express.
    - `note-server-deployment.yaml`: Deploys the Note API server.
    - `note-deployment.yaml`: Deploys the Note frontend application.
  - **Services**:
    - `mongodb-service.yaml`: Exposes MongoDB within the cluster.
    - `mongo-express-service.yaml`: Exposes Mongo Express.
    - `note-server-service.yaml`: Exposes the Note API server.
    - `note-service.yaml`: Exposes the Note frontend application.
  - **Secrets**:
    - `app-secret.yaml`: Stores sensitive data like database credentials.
  - **Config Maps**:
    - `app-config.yaml`: Stores application configurations like database URLs.

## Prerequisites

- Kubernetes Cluster
- Helm 3.x
- kubectl

## Installation

1. Clone the repository:
    ```
    git clone <repository-url>
    cd kubernetes-demo
    ```
2. Deploy the chart using Helm:
    ```
    helm install kubernetes-demo kubernetes-demo/
    ```
3. Verify the deployments:
    ```
    kubectl get deployments
    kubectl get pods
    ```
4. Verify the services:
    ```
    kubectl get services
    ```
5. Verify the configMap and secrets:
    ```
    kubectl get configmap
    kubectl get secrets
    ```
6. Access Mongo Express: Forward the Mongo Express service to your local machine:
    ```
    minikube service <service_name>
    ```

## Cleanup

To uninstall the application, run:
    ```
    helm uninstall kubernetes-demo
    ```

## Notes

- Ensure the `mongo-url` in the ConfigMap and services is correctly configured for inter-service communication.
- Sensitive data is stored in Kubernetes Secrets. Never hardcode credentials in `templates` or `values.yaml`.

## License

## Contributing