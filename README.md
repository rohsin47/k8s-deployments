## k8s-deployments

### CREATE AND INSPECT PODS
* kubectl create -f pod.yml --save-config
* kubectl describe pod <pod-name>
* kubectl apply -f pod.yml
* kubectl exec <pod-name> -it sh
* kubectl edit -f pod.yml
* kubectl delete -f pod.yml
* kubectl delete <pod-name>
* kubectl get pods
* kubectl get pod <pod-name>
* kubectl get pod <pod-name> -o yaml


### DEPLOYMENTS
* kubectl create -f deployment.yml --save-config
* kubectl apply -f deployment.yml
* kubectl get deployments
* kubectl get deployments --show-labels
* kubectl get deployments -l app=my-nginx
* kubectl scale -f deployment.yml --replicas=2


### DEPLOYMENT OPTIONS
* Rolling updates
* Blue-Green deployments
* Canary deployments
* Rollbacks