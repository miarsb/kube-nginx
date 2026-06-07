# kube-nginx README
## Notes
* Instructions are for minikube running on a Windows machine
## Instructions for Startup
* Check if minikube is running:
```
minikube status
```
* (optional) Start minikube
```
minikube start
```
* Configure volume mount for nginx to access our site(make sure to do this in a seperate window):
```
minikube mount C:\path\to\repo\site:/mnt/data
```
* Create configmap:
```
kubectl create -f C:\path\to\repo\kube-nginx-config.yaml
```
* Create secret:
```
kubectl create -f C:\path\to\repo\secrets.yaml
```
* Create deployment using YAML file:
```
kubectl create -f C:\path\to\repo\deployment.yaml
```
* Create Service to expose nginx:
```
kubectl expose deployment/kube-nginx --type="LoadBalancer" --port 8080 --target-port 80
```
* Create tunnel to access node(make sure to do this in a seperate window):
```
minikube tunnel
```
* Create ingress:
```
kubectl create -f C:\path\to\repo\ingress.yaml
```
* Check if site is available:
```
curl http://127.0.0.1:8080/
```
## Instructions for cleanup
* Cancel tunnel command/close terminal
* Cancel mount command/close terminal
* Delete service:
```
kubectl delete service kube-nginx
```
* Delete Deployment:
```
kubectl delete deployment kube-nginx
```
* Delete ConfigMap:
```
kubectl delete configmap kube-nginx-config
```
* Delete Secret:
```
kubectl delete secret db-user-pass
```
