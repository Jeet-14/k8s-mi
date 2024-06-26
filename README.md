# k8s-mi
k8s migration test


kind-cluster - for cluster config
Appset - for 'application' on argo
chart - helm chart for cronjob 
kubent- report against diff k8s versions
Que - question/query


```bash
cd kind-cluster
kind create cluster --config kind-cluster.yaml
```


ArgoCD install & expose
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

kubectl port-forward svc/argocd-server -n argocd 8080:443
```