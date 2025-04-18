# Go Web Service on Google Kubernetes Engine (GKE)

This project is a simple, secure Go-based web service deployed to Google Kubernetes Engine (GKE) using Docker and Kubernetes.

## Features

- Minimal Go HTTP server (`Hello, secure GKE world!`)
- Containerized with multi-stage Docker build using a `distroless` base image
- Hosted on GKE Autopilot with load-balanced access
- Deployment managed via Kubernetes manifests

## Quick Start

### 1. Build and Push Image

```bash
docker build --platform=linux/amd64 -t us-central1-docker.pkg.dev/<PROJECT_ID>/go-gke-demo-repo/server:latest .
docker push us-central1-docker.pkg.dev/<PROJECT_ID>/go-gke-demo-repo/server:latest
```

### 2. Create GKE Autopilot Cluster

```bash
gcloud container clusters create-auto go-demo-cluster --region=us-central1
gcloud container clusters get-credentials go-demo-cluster --region=us-central1
```

### 3. Deploy to GKE

```bash
kubectl apply -f k8s-deployment.yaml
```

### 4. Access the Service

```bash
kubectl get svc hello-service
curl http://<EXTERNAL-IP>/
```

## Files

- `main.go`: Go web server source code
- `Dockerfile`: Multi-stage Docker build
- `k8s-deployment.yaml`: Kubernetes Deployment and Service

## License

MIT
