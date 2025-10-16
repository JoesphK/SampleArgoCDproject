# SampleArgoCDproject

A sample project for deploying **nginx** using **Argo CD** as a GitOps deployment demonstration. Ideal for testing validation with ArgoCD.

---

## Table of Contents

- [Overview](#overview)  
- [Architecture](#architecture)  
- [Prerequisites](#prerequisites)  
- [Installation & Deployment](#installation--deployment)  



---

## Overview

This is a proof-of-concept repository to showcase how to deploy a simple nginx application using Argo CD.  
It demonstrates the GitOps model, where application configuration is stored in Git, and Argo CD syncs and manages the infrastructure and app state.

---

## Architecture

1. This repository contains Kubernetes manifest files describing the nginx deployment, service, and app configuration.  
2. Argo CD watches a target branch in the repository and syncs the manifests into a Kubernetes cluster.  
3. Changes pushed to Git are automatically applied by Argo CD to reconcile the live cluster state.

---

## Prerequisites

Before using this project, ensure you have:

- A running Kubernetes cluster (example: minikube, EKS, GKE, etc.)  
- Argo CD installed and running in the cluster  
- A localhost port-forward or external access to the Argo CD UI  

---

## Installation & Deployment
- Under ArgoCD, create a new repository
- Attach the github link to the projects
- Under ArgoCD create a new application
- Specify the project
- Specify which edition, Dev or Production
- Sync the project
