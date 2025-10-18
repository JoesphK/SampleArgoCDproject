# Dependency Track deployer  

---

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Tools Used](#tools-used)
- [Prerequisites](#prerequisites)
- [Installation & Deployment](#installation--deployment)
 

---

## Overview

This application is used to easily deploy dependency track's frontend and backend together using ArgoCD. Refer to these two repositories for more information:  
Backend: https://github.com/JoesphK/Container-DT-Backend  
Frontend: https://github.com/JoesphK/Container-DT-Frontend  
---

  
## Tools used

[![Argo CD](https://img.shields.io/badge/Argo%20CD-ef7b4d?logo=argo&logoColor=white)](https://argoproj.github.io/cd/)  
[![Kustomize](https://img.shields.io/badge/Kustomize-326ce5?logo=kubernetes&logoColor=white)](https://kustomize.io/)  
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326ce5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)  


---  

## Project Structure
.  
├── base/  
│   ├── deployment.yaml  
│   ├── service.yaml  
│   └── kustomization.yaml  
├── overlay/  
│   ├── dev/  
│   │   └── kustomization.yaml  
│   └── production/  
│       └── kustomization.yaml  
└── README.md  


---  

## Architecture

The project follows a GitOps workflow:

1. **Kustomize** manages environment-specific configurations (e.g., dev, production).  
2. **Argo CD** continuously monitors this repository for changes.  
3. When updates are pushed to Git, Argo CD automatically syncs the manifests into the **Kubernetes** cluster.  
4. **This project** will be used to deploy the application as a whole

```mermaid
flowchart LR
    A[Git Repository] -->|Sync| B[Argo CD]
    B --> |Update| C[Kubernetes Cluster]
    C --> |Deploy| D[Dependency track Service]
```

---  

## Prerequisites

Before using this project, ensure you have:

- A running Kubernetes cluster  
- Argo CD installed and running in the cluster  
- An external access to the Argo CD UI. 

---

## Installation & Deployment

1. **Add this repository to Argo CD**
   - In the Argo CD UI, go to **Settings → Repositories → Connect Repo**.
   - Paste the GitHub URL of this project.

2. **Create a new Argo CD Application**
   - In the Argo CD UI, click **New App**.
   - Set the repository URL to this repo.
   - Choose the desired path:
     - `kustomize/overlays/dev` for development
     - `kustomize/overlays/production` for production
   - Choose your target cluster and namespace.

3. **Sync the application**
   - Click **Sync** to deploy Nginx automatically.
   - Open [http://PUBLIC-IP](http://PUBLIC-IP) in your browser.
