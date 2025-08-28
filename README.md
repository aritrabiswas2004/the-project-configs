# Configurations for The Project

This repository only contains all the YAML configuration files for The Project.

See the [code repository](https://github.com/aritrabiswas2004/mooc-the-project) for the code.

## Deploying via ArgoCD

### Install ArgoCD

Get ArgoCD up and running with the command

```shell
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### Deployment

To deploy the project with ArgoCD, run

```shell
kubectl apply -n argocd -f application.yaml
```

By default, the manifest points to the staging overlay.
To deploy to production, update `application.yaml` as below

```yaml
source:
  repoURL: https://github.com/aritrabiswas2004/mooc-the-project
  path: overlays/prod   # change from overlays/staging
  targetRevision: HEAD

destination:
  server: https://kubernetes.default.svc
  namespace: production # change from staging if desired
```
