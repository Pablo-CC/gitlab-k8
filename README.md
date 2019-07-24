# Gitlab K8 Instance

## TL;DR;
Install Tiller:
```
# Create service account for Tiller
kubectl -n kube-system create serviceaccount tiller
# Grant cluster-admin role to service account
kubectl create clusterrolebinding tiller-cluster-admin \
    --clusterrole=cluster-admin \
    --serviceaccount=kube-system:tiller
# Start Tiller
helm init --service-account tiller --upgrade
# Wait for Tiller to start
kubectl -n kube-system wait --for condition=ready pods -l "app=helm,name=tiller" --timeout 300s
```

Deploy scenario into Kubernetes:
```
git clone https://github.com/Pablo-CC/gitlab-k8.git
kubectl apply -f pvs.yaml
kubectl apply -f pvc.yaml
helm repo add gitlab https://charts.gitlab.io/
helm install --name=gitlab gitlab/gitlab -f values.yaml
```
