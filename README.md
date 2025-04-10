# Kubernetes AI Compose

A scalable, containerized AI chatbot application deployed on Kubernetes, featuring a modern web interface, backend API, and an AI model service.

## 🌟 Features

- Containerized AI chatbot using Ollama
- Kubernetes-native deployment
- Scalable microservices architecture
- Persistent storage for AI model data
- Load balancing and service discovery
- Health monitoring and auto-recovery
- Modern web interface

## 🏗️ Architecture

The application consists of three main components:

1. **Frontend Service**: Web interface for user interactions
2. **Backend Service**: API service handling request processing and communication
3. **Model Service**: AI model service powered by Ollama

## 🛠️ Prerequisites

- Kubernetes cluster (v1.19+)
- kubectl CLI tool
- Docker (for local development)
- Minimum 8GB RAM for the model service
- Storage provisioner for persistent volumes

## 📦 Components

### Deployments
- `frontend-deployment.yaml`: Web interface deployment
- `backend-deployment.yaml`: API service deployment
- `model-deployment.yaml`: AI model service deployment

### Configuration
- `configmap.yaml`: Application configuration
- `model-pv.yaml`: Persistent volume configuration for model data

### Services
- Frontend Service (LoadBalancer)
- Backend Service (ClusterIP)
- Model Service (ClusterIP)

## 🚀 Deployment

1. Clone the repository:
```bash
git clone <repository-url>
cd Kubernetes-AI-Compose
```

2. Deploy the application using the provided script:
```bash
chmod +x deploy.sh
./deploy.sh
```

The script will:
- Create the `ai-compose` namespace
- Apply ConfigMap configurations
- Set up persistent storage
- Deploy all services
- Monitor deployment status
- Provide the frontend service URL

## 🔍 Monitoring

Monitor the deployment status:
```bash
kubectl get pods -n ai-compose
kubectl get services -n ai-compose
```

View application logs:
```bash
kubectl logs -f deployment/frontend -n ai-compose
kubectl logs -f deployment/backend -n ai-compose
kubectl logs -f deployment/model -n ai-compose
```

## 🔧 Configuration

The application can be configured through the `configmap.yaml` file:
- MODEL: Specify the AI model to be used
- Other environment variables as needed

## 📊 Resource Requirements

- Model Service: 4-8GB RAM
- Backend Service: Default resource allocation
- Frontend Service: Default resource allocation

## 🛟 Troubleshooting

1. If pods are not starting:
   ```bash
   kubectl describe pod <pod-name> -n ai-compose
   ```

2. If services are not accessible:
   ```bash
   kubectl get events -n ai-compose
   ```

3. For persistent volume issues:
   ```bash
   kubectl get pv,pvc -n ai-compose
   ```

## 🔒 Security Considerations

- The model service is not exposed externally
- All inter-service communication is within the cluster
- Configure network policies as needed for your environment
- Review and adjust resource limits based on usage

