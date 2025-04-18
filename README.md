# Best Buy Cloud-Native Application Demo - Final Lab Assignment CST8915

## 📦 Project Overview

This cloud-native application simulates Best Buy’s online cloud-native application, using a microservices architecture. The application supports product browsing, ordering, admin operations, and order fulfillment. It also features AI-powered product description and image generation using GPT-4 and DALL·E.

This project is a customized version of the **Algonquin Pet Store (On Steroids)** architecture, with key improvements:
- Slightly modified the store-front and store-admin user interface to reflect best buy related products
- Replaced RabbitMQ with **Azure Service Bus**
- Added AI-Service using **Azure OpenAI (GPT-4 + DALL·E)**

---

## 🧱 Application Architecture

![Best buy cloud native demo Architecture Diagram](./assets/best-buy-demo-cloud-native.png)

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

- Kubernetes cluster(Azure Kubernetes Service)
- `kubectl` configured to target your cluster
- Docker Hub or Azure Container Registry access
- Azure Service Bus queue created
- Azure OpenAI resource provisioned

### 📤 Deploy to Kubernetes

```bash
# Step 1: Apply ConfigMaps and Secrets
kubectl apply -f Deployment\ Files/configmaps.yaml
kubectl apply -f Deployment\ Files/secrets.yaml



# Step 2: Deploy microservices
kubectl apply -f Deployment\ Files/aps-all-in-one.yaml

---

## 🔗 Microservice Repositories

| Service           | Repository Link                   |
|-------------------|-----------------------------------|
| Store-Front       | [https://github.com/kare0041/store-front-best-buy.git]                     |
| Store-Admin       | [https://github.com/kare0041/store-admin-best-buy.git]                     |
| Product-Service   | [https://github.com/kare0041/product-service-best-buy.git]                     |
| Order-Service     | [https://github.com/kare0041/order-service-best-buy.git]                     |
| Makeline-Service  | [https://github.com/kare0041/makeline-service-best-buy.git]                     |
| AI-Service        | [https://github.com/kare0041/ai-service-best-buy.git]                     |

---

## 🐳 Docker Images

| Service           | Docker Image Link                 |
|-------------------|-----------------------------------|
| Store-Front       | [https://hub.docker.com/repository/docker/kadanielo/store-front-best-buy/general]                 |
| Store-Admin       | [https://hub.docker.com/repository/docker/kadanielo/store-admin-best-buy/general]                 |
| Product-Service   | [https://hub.docker.com/repository/docker/kadanielo/product-service-best-buy/general]                 |
| Order-Service     | [https://hub.docker.com/repository/docker/kadanielo/order-service-best-buy/general]                 |
| Makeline-Service  | [https://hub.docker.com/repository/docker/kadanielo/makeline-service-best-buy/general]                 |
| AI-Service        | [https://hub.docker.com/repository/docker/kadanielo/ai-service-best-buy/general]                 |

---

## 📹 Demo Video

Watch the 5-minute demo here:  
🔗 [YouTube Demo Link](https://youtu.be/I0-3yg4N6v4)

---

## ⚠️ Known Issues or Limitations

- GPT-4 AI-Service is not generating product descriptions accordingly.
- Integration with Azure Service Bus is not working as expected, after upding the aps-all-in-one.yaml file with ORDER_QUEUE environment variables.

