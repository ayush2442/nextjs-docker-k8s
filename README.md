# Next.js Docker Kubernetes Deployment

This project shows how to containerize a Next.js app (basic starter template) using Docker, set up CI/CD with GitHub Actions, and deploy it locally on Kubernetes using Minikube.

## Prerequisites
- Node.js 18+
- Docker
- Minikube
- kubectl
- GitHub account

## Local Development
```bash
# Install dependencies
npm install

# Run the dev server
npm run dev

# Build for production
npm run build
```

## Docker Setup
```bash
# Build Docker image
docker build -t nextjs-app:latest .

# Run container locally
docker run -p 3000:3000 nextjs-app:latest
```

## CI/CD with GitHub Actions
- On every push to main, a Docker image is built and pushed to GitHub Container Registry (GHCR).
- Image URL format: ghcr.io/ayush2442/nextjs-docker-k8s:latest

## Deploy to Kubernetes (Minikube)
```bash
# Start Minikube
minikube start

# Update image in deployment.yaml
# Apply manifests
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

# Check resources
kubectl get pods
kubectl get services

# Access app
minikube service nextjs-service --url
```

## Cleanup
```bash
kubectl delete -f k8s/
minikube stop
```
