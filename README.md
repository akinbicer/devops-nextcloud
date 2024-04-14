# NextCloud Application

This project allows you to create your own personal cloud storage service using the Nextcloud cloud storage solution. It provides instructions for deploying Nextcloud using both Docker Compose and Kubernetes.

## Docker Compose Installation

### Prerequisites

Before starting the installation, ensure that you have the following prerequisites installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Step 1: Clone the Repository

```bash
git clone https://github.com/akinbicer/devops-nextcloud.git
cd devops-nextcloud
```

### Step 2: Start the Project with Docker Compose

```bash
docker-compose up -d
```

### Step 3: Access Nextcloud

Open your web browser and go to `http://localhost`. You will see the Nextcloud setup screen. Complete the installation by providing the necessary information.

### Step 4: Database Connection

Use the following information for the database connection:

- Database Type: MySQL/MariaDB
- Database Host: `db`
- User: `nextcloud`
- Password: `BpW8yOrbJc0NjIvi2GKcCFtyYVFagodIx4ljrBT5Jyn8u2LlLt`
- Database Name: `nextcloud`

## Kubernetes Installation

### Prerequisites

Before starting the installation, ensure that you have the following prerequisites installed:

- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Helm](https://helm.sh/docs/intro/install/)

### Step 1: Deploy MySQL/MariaDB Database

Apply the following YAML files to your Kubernetes cluster:

```bash
kubectl apply -f deploys/kubernetes/persistentvolume-db-pv.yaml
kubectl apply -f deploys/kubernetes/persistentvolumeclaim-db-pvc.yaml
kubectl apply -f deploys/kubernetes/secret-db.yaml
kubectl apply -f deploys/kubernetes/deployment-cloud-database.yaml
```

### Step 2: Deploy Nextcloud Application

Apply the following YAML files to your Kubernetes cluster:

```bash
kubectl apply -f deploys/kubernetes/secret-db-secret.yaml
kubectl apply -f deploys/kubernetes/deployment-cloud-app.yaml
kubectl apply -f deploys/kubernetes/service-cloud-app.yaml
```

### Step 3: Access Nextcloud

Obtain the IP address of the Nextcloud service:

```bash
minikube service cloud-app --url
```

Open the provided URL in your web browser to access Nextcloud.

## Important Notes

- Ensure that the PersistentVolume (PV) and PersistentVolumeClaim (PVC) are configured according to your storage requirements.
- Customize the database credentials and other configurations in the respective YAML files before applying them to your Kubernetes cluster.

## License
This project is licensed under the MIT License. For more information, see the [LICENSE](LICENSE) file.

## Issues, Feature Requests or Support
Please use the [New Issue](https://github.com/akinbicer/devops-nextcloud/issues/new) button to submit issues, feature requests or support issues directly to me. You can also send an e-mail to akin.bicer@outlook.com.tr.