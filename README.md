# Best Buy Cloud-Native Application Demo - Final Lab Assignment CST8915

## 📦 Project Overview

This cloud-native application simulates Best Buy’s online store using a microservices architecture. The application supports product browsing, ordering, admin operations, and order fulfillment. It also features AI-powered product description and image generation using GPT-4 and DALL·E.

This project is a customized version of the **Algonquin Pet Store (On Steroids)** architecture, with key improvements:
- 📨 Replaced RabbitMQ with **Azure Service Bus**
- 🤖 Added AI-Service using **Azure OpenAI (GPT-4 + DALL·E)**

---

## 🧱 Application Architecture

![Architecture Diagram](./assets/architecture-diagram.png)

The architecture consists of multiple microservices deployed on a Kubernetes cluster:

| Component        | Description                                      |
|------------------|--------------------------------------------------|
| Store-Front      | Customer-facing UI for product browsing & orders |
| Store-Admin      | Admin UI for managing products & viewing orders  |
| Product-Service  | Handles product CRUD operations                  |
| Order-Service    | Sends order details to Azure Service Bus         |
| Makeline-Service | Consumes from Azure Service Bus and completes orders |
| AI-Service       | Uses GPT-4 for descriptions & DALL·E for images  |
| MongoDB          | Stores product and order data                    |

---

## 🚀 Deployment Instructions

Follow these steps to deploy the application to a Kubernetes cluster.

### 🔧 Prerequisites

- Kubernetes cluster (e.g., Azure Kubernetes Service or Minikube)
- `kubectl` configured to target your cluster
- Docker Hub or Azure Container Registry access
- Azure Service Bus queue created
- Azure OpenAI resource provisioned

### 📤 Deploy to Kubernetes

```bash
# Step 1: Apply ConfigMaps and Secrets
kubectl apply -f Deployment\ Files/configmaps.yaml
kubectl apply -f Deployment\ Files/secrets.yaml

# Step 2: Deploy MongoDB
kubectl apply -f Deployment\ Files/mongo-statefulset.yaml

# Step 3: Deploy microservices
kubectl apply -f Deployment\ Files/store-front-deployment.yaml
kubectl apply -f Deployment\ Files/store-admin-deployment.yaml
kubectl apply -f Deployment\ Files/product-service-deployment.yaml
kubectl apply -f Deployment\ Files/order-service-deployment.yaml
kubectl apply -f Deployment\ Files/makeline-service-deployment.yaml
kubectl apply -f Deployment\ Files/ai-service-deployment.yaml

# Step 4: Expose services (use Ingress or NodePort)
kubectl apply -f Deployment\ Files/ingress.yaml
```

---

## 🔗 Microservice Repositories

| Service           | Repository Link                   |
|-------------------|-----------------------------------|
| Store-Front       | [GitHub Link]                     |
| Store-Admin       | [GitHub Link]                     |
| Product-Service   | [GitHub Link]                     |
| Order-Service     | [GitHub Link]                     |
| Makeline-Service  | [GitHub Link]                     |
| AI-Service        | [GitHub Link]                     |

---

## 🐳 Docker Images

| Service           | Docker Image Link                 |
|-------------------|-----------------------------------|
| Store-Front       | [Docker Hub Link]                 |
| Store-Admin       | [Docker Hub Link]                 |
| Product-Service   | [Docker Hub Link]                 |
| Order-Service     | [Docker Hub Link]                 |
| Makeline-Service  | [Docker Hub Link]                 |
| AI-Service        | [Docker Hub Link]                 |

---

## 📹 Demo Video

Watch the 5-minute demo here:  
🔗 [YouTube Demo Link](https://youtube.com/example-demo)

---

## ⚠️ Known Issues or Limitations

- AI-Service requires a stable internet connection and valid API keys.
- Limited error-handling in the demo version.
- Orders may take a few seconds to process via the queue.

---

## 📁 Deployment Files

All Kubernetes YAML files are located in the `/Deployment Files` folder.

```
Deployment Files/
├── ai-service-deployment.yaml
├── configmaps.yaml
├── ingress.yaml
├── makeline-service-deployment.yaml
├── mongo-statefulset.yaml
├── order-service-deployment.yaml
├── product-service-deployment.yaml
├── secrets.yaml
├── store-admin-deployment.yaml
└── store-front-deployment.yaml
```
