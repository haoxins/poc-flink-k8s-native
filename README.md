
## PoC: K8s native Flink cluster deployment and job management

* [Apache Flink Kubernetes Operator](https://github.com/apache/flink-kubernetes-operator)
* [Argo CD](https://github.com/argoproj/argo-cd)
* [Istio](https://github.com/istio/istio)

* Why split Flink Operator into two Argo CD applications?
  - See [here](https://github.com/prometheus-operator/prometheus-operator/issues/4439)

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
