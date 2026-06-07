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
* Configure volume mount for nginx to access our site:
```
minikube mount C:/path/to/loca/site:/mnt/data
```
* Create deployment using YAML file:
```
kubectl apply -f C:/Users/Brando/Documents/repos/kube-nginx/deployment.yaml
```
* Create Service to expose nginx:
```
kubectl expose deployment/kube-nginx --type="LoadBalancer" --port 8080 --target-port 80
```
* Create tunnel to access node
```
minikube tunnel
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
