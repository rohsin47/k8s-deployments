# k8s-deployments

## CREATE AND INSPECT PODS
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