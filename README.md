# Gitlab K8 Instance

## TL;DR;
```
git clone https://github.com/Pablo-CC/gitlab-k8.git
kubectl apply -f pvs.yaml
kubectl apply -f pvc.yaml
helm repo add gitlab https://charts.gitlab.io/
helm install --name=gitlab gitlab/gitlab -f values.yaml
```
