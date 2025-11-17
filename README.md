# voting-app-project-k8s
voting-app-project-k8s-cluster
# Voting App - Kubernetes Deployment

This repository contains Kubernetes manifests for deploying the **Voting Application** onto any Kubernetes cluster.

The application includes:

- Vote frontend (UI for casting votes)
- Result frontend (UI for displaying results)
- Redis (queue backend)
- Worker (processes votes)
- Postgres (database)
- Postgres persistent storage

---

## 🚀 How to Deploy

### 1. Create Namespace


### 2. Deploy All Services

- kubectl apply -f redis/
- kubectl apply -f postgres/
- kubectl apply -f vote/
- kubectl apply -f result/
- kubectl apply -f worker/


### 3. Verify Resources

- kubectl get pods -n voting-app
- kubectl get svc -n voting-app
- kubectl get pvc -n voting-app

  
### 4. Access the Application

- Vote UI → LoadBalancer or NodePort (Service: **vote**)  
- Result UI → LoadBalancer or NodePort (Service: **result**)

---

## 📁 Folder Structure

voting-app-k8s/
├── namespace.yaml
├── redis/
├── postgres/
├── vote/
├── result/
└── worker/


Each folder contains **Deployment** and **Service** YAML files.

---

## 🛠 Customize Docker Images

Update image names inside:

- `vote/vote-deployment.yaml`
- `result/result-deployment.yaml`
- `worker/worker-deployment.yaml`

Example:


---

## 🧹 Clean Up the Cluster


This removes EVERYTHING.

---

## 🔥 Need Helm Chart Version?

I can generate a complete **Helm chart** structure as well

voting-app-k8s/
├── README.md
├── namespace.yaml
├── k8s-base/                             # plain kubernetes manifests (for direct kubectl apply)
│   ├── redis/
│   │   ├── redis-deployment.yaml
│   │   └── redis-service.yaml
│   ├── postgres/
│   │   ├── postgres-pvc.yaml
│   │   ├── postgres-deployment.yaml
│   │   └── postgres-service.yaml
│   ├── vote/
│   │   ├── vote-deployment.yaml
│   │   └── vote-service.yaml
│   ├── result/
│   │   ├── result-deployment.yaml
│   │   └── result-service.yaml
│   ├── worker/
│   │   └── worker-deployment.yaml
│   ├── config/
│   │   ├── voting-configmap.yaml
│   │   └── voting-secret.yaml
│   ├── ingress/
│   │   └── ingress-nginx.yaml
│   └── hpa/
│       └── hpa.yaml
│
├── helm-chart/                           # full Helm Chart named voting-app
│   ├── Chart.yaml
│   ├── values.yaml
│   └── templates/
│       ├── namespace.yaml
│       ├── configmap.yaml
│       ├── secret.yaml
│       ├── redis-deployment.yaml
│       ├── redis-service.yaml
│       ├── postgres-pvc.yaml
│       ├── postgres-deployment.yaml
│       ├── postgres-service.yaml
│       ├── vote-deployment.yaml
│       ├── vote-service.yaml
│       ├── result-deployment.yaml
│       ├── result-service.yaml
│       ├── worker-deployment.yaml
│       ├── ingress.yaml
│       └── hpa.yaml
│
├── cicd/
│   ├── .github/
│   │   └── workflows/
│   │       └── ci-cd.yml                # GitHub Actions
│   └── jenkins/
│       └── Jenkinsfile
│
├── istio/                                # simple Istio resources (optional)
│   ├── gateway.yaml
│   └── virtualservice.yaml
│
└── docs/
    └── production-notes.md


