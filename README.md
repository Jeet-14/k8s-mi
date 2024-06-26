# k8s-mi
k8s migration test


kind-cluster - for cluster config
Appset - for 'application' on argo (Not needed)
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

ArgoCD login and Create App
```bash
argocd login localhost:8080 --username admin --password 6E########aZ  --insecure


argocd app create my-app \
--repo https://github.com/Jeet-14/k8s-mi \
--path chart/mychart/nginx \
--dest-server https://kubernetes.default.svc \
--dest-namespace default \
--sync-policy automated


```

Run kubent

```bash
 kubent --target-version 1.28.2 >> kubent/kubent_report_target_1_28_2.txt
```


------------------------------------------------------------------------------------


Created a new cluster v1.27, deployed argo and application as well.

