## Deploying an Argo CD instance from a Pull Request


### Build & Deploy

1. Identity the PR you wish to deploy. Example, https://github.com/argoproj/argo-cd/pull/5142

2. Grab the branch associated with it and run the following in the context of namespace `foo`.

```
helm install --generate-name  argocd-dev-branch --set source_url=https://github.com/farodin91/argo-cd --set ref=health-checks-cluster-api
```


### Navigate


3. Wait for the image to be built:

```
$ kubectl get builds
NAME        TYPE     FROM          STATUS    STARTED          DURATION
argo-cd-1   Docker   Git@12a1e0b   Running   12 minutes ago   
```


4. Find the deployed Ingress/Route by doing an `oc get route argocd`:

```
$ kubectl get routes 
NAME     HOST/PORT                                                    PATH   SERVICES        PORT    TERMINATION        WILDCARD
argocd   argocd-t4.apps.dev-svc-4.8-032414.devcluster.openshift.com          argocd-server   https   passthrough/None   None
```
