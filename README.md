# E-commerce Microservices Platform on AWS EKS

## Overview
Deployed Google's Online Boutique, a cloud-native 11-microservice e-commerce application, on a self-provisioned Amazon EKS (Elastic Kubernetes Service) cluster, simulating a real production environment.

## Problem Statement
Modern applications need to handle server failures, traffic spikes, and service-to-service communication reliably without manual intervention. This project demonstrates deploying and managing a multi-service application using managed Kubernetes infrastructure on AWS.

## Architecture
- 11 microservices (Go, Java, Python, Node.js, C#) communicating via gRPC
- Services: Frontend, Cart, Checkout, Payment, Shipping, Currency, Email, Recommendation, Ad, Product Catalog, Redis
- AWS EKS cluster: 3 worker nodes (t3.small, managed node group)
- Exposed to the internet via AWS Network Load Balancer
- Deployed in a dedicated Kubernetes namespace for isolation

## What I Implemented
- Provisioned EKS cluster using eksctl (Infrastructure as Code approach)
- Configured IAM user with least-privilege CLI access (avoided root account usage)
- Deployed multi-container microservices architecture via kubectl
- Verified self-healing: manually deleted a pod and confirmed Kubernetes automatically recreated it within seconds
- Performed manual horizontal scaling of the frontend service
- Used namespace isolation to separate this workload from other resources
- Practiced cost-conscious cloud usage: cluster created, tested, and torn down same-day to avoid unnecessary billing

## Tech Stack
Docker | Kubernetes | AWS EKS | eksctl | kubectl | gRPC | AWS IAM | AWS Load Balancer

## Key Learnings
- Real-world AWS EKS cluster provisioning and node group management
- Microservices networking and service discovery in Kubernetes
- Kubernetes self-healing and scaling behavior under failure conditions
- Cloud cost management and resource cleanup discipline

## Screenshots

### Cluster Nodes Running
![EKS Nodes](screenshots/nodes.png)

### Live Application
![Live App](screenshots/liveapp.png)

### Pods Running
![Pods Running](screenshots/podsrunning.png)

### Self-Healing Test
![Self Healing](screenshots/healing.png)

### Services with Load Balancer
![Services](screenshots/services.png)

## Cleanup
eksctl delete cluster --name online-boutique --region ap-south-1
