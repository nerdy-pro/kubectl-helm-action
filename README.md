# kubectl-helm-action

[![Page Views Count](https://badges.toozhao.com/badges/01G1FYS3PGTQG8FS69ZZVS7MZR/green.svg)](https://badges.toozhao.com/stats/01G1FYS3PGTQG8FS69ZZVS7MZR "Get your own page views count badge on badges.toozhao.com")

A Github action for using kubectl and helm to deploy applications to Kubernetes cluster

## How to use

### Config a Github workflow

Create a workflow file `.github/workflows/deploy.yaml`

```yaml
on: push
name: deploy
jobs:
  deploy:
    name: deploy to cluster
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: deploy to cluster
      uses: wahyd4/kubectl-helm-action@master
      with:
        args: kubectl apply -f manifest.yaml
```

Or you may want to deploy applications with `helm`

```yaml
- name: deploy postgres to cluster
  uses: wahyd4/kubectl-helm-action@master
  with:
    args: |
      helm repo add bitnami https://charts.bitnami.com/bitnami
      helm upgrade --install postgres -n data bitnami/postgresql

```

## Thanks

This repo is inspired by [steebchen/kubectl](https://github.com/steebchen/kubectl), thanks.
