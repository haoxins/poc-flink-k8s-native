
## PoC: K8s native Flink cluster deployment and job management

* [spotify/flink-on-k8s-operator](https://github.com/spotify/flink-on-k8s-operator)
  - An open source fork of [GoogleCloudPlatform/flink-on-k8s-operator](https://github.com/GoogleCloudPlatform/flink-on-k8s-operator)

* [Argo CD](https://github.com/argoproj/argo-cd)
* [Istio](https://github.com/istio/istio)
  - [oidc-filter](https://github.com/dgn/oidc-filter)
* [Dex](https://github.com/dexidp/dex)

### Install Argo CD

```zsh
k apply -k argocd
```

### Install compoments

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
