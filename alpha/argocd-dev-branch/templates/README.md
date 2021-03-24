## Deploying an Argo CD instance from a Pull Request

1. Identity the PR you wish to deploy. Example, https://github.com/argoproj/argo-cd/pull/5142

2. Grab the branch associated with it and run the following in the context of namespace `foo`.

```
helm install --generate-name  argocd-dev-branch --set source_url=https://github.com/farodin91/argo-cd --set ref=health-checks-cluster-api
```