
## PoC: K8s native Flink cluster deployment and job management

* [Argo CD](https://github.com/argoproj/argo-cd)
* [spotify/flink-on-k8s-operator](https://github.com/spotify/flink-on-k8s-operator)
* [Istio](https://github.com/istio/istio)

### Install Argo CD

```zsh
k apply -k argocd
```

### Install PoC

```
k apply -f poc.yaml
```

### Access the Argo CD UI

```zsh
k port-forward svc/argocd-server \
  -n argocd 8080:443
# Username: admin
# Get password
k get secret argocd-initial-admin-secret \
  -n argocd \
  -o jsonpath="{.data.password}" | base64 -d
```
