# ArgoCD ApplicationSet Helm Template

This repository contains templates for deploying multiple applications to a local Kubernetes cluster (like Minikube or Kind) using ArgoCD ApplicationSet and Helm charts.

## Repository Structure

```
.
├── .gitignore
├── README.md
├── argocd
│   ├── applicationset.yaml
│   └── bootstrap.yaml
├── charts
│   ├── app1
│   │   ├── Chart.yaml
│   │   └── values.yaml
│   ├── app2
│   │   ├── Chart.yaml
│   │   └── values.yaml
│   └── base
│       ├── Chart.yaml
│       ├── templates
│       │   ├── deployment.yaml
│       │   └── service.yaml
│       └── values.yaml
└── environments
    ├── dev
    │   └── values.yaml
    └── prod
        └── values.yaml
```

## Usage

1.  **Install ArgoCD:** Follow the official ArgoCD documentation to install it on your cluster.
2.  **Bootstrap ApplicationSet:** Apply the bootstrap application to deploy the ApplicationSet controller:
    ```bash
    kubectl apply -f argocd/bootstrap.yaml -n argocd
    ```
3.  **Customize:** Modify the Helm charts and environment values according to your needs.
4.  **Commit and Push:** Commit the changes to your Git repository.
5.  **Sync:** ArgoCD will automatically detect the ApplicationSet and deploy the applications defined for each environment. 