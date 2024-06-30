# DevOps Assignment - Kubernetes Config for Clickhouse & Superset

## Overview

This repository contains the Kubernetes configurations required to launch Clickhouse and Superset pods in Minikube and connect them. The project demonstrates the deployment of Clickhouse with persistent storage and the integration of Superset for BI reporting.

## Prerequisites

- Kubernetes knowledge
- Minikube installed on your local machine
- Docker installed on your local machine
- Basic understanding of Clickhouse and Superset

## Setup Instructions

### Step 1: Clone the Repository

git clone https://github.com/YOUR_USERNAME/compilerd.git
cd compilerd

### Step 2: Start Minikube

Ensure that Minikube is running:
minikube start --driver=docker
### Step 3: Create Kubernetes Namespace
kubectl create namespace data-analytics
### Step 4: Deploy Clickhouse

1. **Persistent Volume Claim**

   Create a Persistent Volume Claim for Clickhouse
   kubectl apply -f clickhouse-pvc.yaml -n data-analytics
   
2. **StatefulSet**

   Deploy Clickhouse using StatefulSet:
   kubectl apply -f clickhouse-statefulset.yaml -n data-analytics


### Step 5: Deploy Superset

Deploy Superset:
kubectl apply -f superset-deployment.yaml -n data-analytics

### Step 6: Access Superset

Get the URL for the Superset Service:
minikube service superset-service -n data-analytics

This command will either open the Superset URL in your default web browser or print the URL to the terminal. Copy and paste the URL into your browser if needed.

### Step 7: Connect Clickhouse to Superset

1. Open the Superset URL in your browser.
2. Go to `Data > Databases > (+Database button)`.
3. Choose Clickhouse from the list.
4. Add the Clickhouse URL in the following format: `clickhouse://default@<clickhouse-service-name>:9000/default`.
5. Click Connect.

### Step 8: Verify the Connection

Ensure that you can query Clickhouse data through Superset.
