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

### SERVICES
- Services abstracts Pod IP addresses from consumers.
- Load balances between Pods.
- Relies on labels to associate a Service with a Pod.
- Node's kube-proxy creates a virtual IP for Services.
- Layer 4 (TCP/IP) of OSI
- Services are not ephemeral.
- Creates endpoints which sit between a Service and Pod.
- Static IP addresses.
- abstraction layer to talk to Pods.
- Service types
    - ClusterIP  
        - expose the service on a cluster-internal IP (default)
        - only pods within cluster can talk to the service
        - allow pods to talk to other pods directly
    - NodePort
        - expose the service on each Node's IP at a static port
        - allocates a port from a range(30000-32767)
        - each node proxies the allocated port
        - not secure, can be used for debugging.
    - LoadBalancer
        - provision an external IP to act as a load balancer for service
        - useful when combined with cloud provider load balancer (Azure, AWS, GCP)
        - NodePort and ClusterIP services are created.
        - Each Node proxies the allocated port.
    - ExternalName 
        - Maps a service to a DNS name
        - alias for an external service
        - external service details are hidden from the cluster
        
- port-forwarding
    - Listen on port 8080 locally and forward to port 80 in Pod -> kubectl port-forward pod/[pod-name] 8080:80
    - Listen on port 8080 locally and forward to Deployment's Pod -> kubectl port-forward  deployment/[deployment-name] 8080:80
    - Listen on port 8080 locally and forward to Service's Pod -> kubectl port-forward service/[service-name] 8080
    
- inside pod and talking to other pods
    - kubectl exec [pod-name-1] -it sh
    - apk add curl
    - curl http://[pod-name-2-ip:port]
- kubectl apply -f service.yml
- kubectl get services
- kubectl delete service <service-name>
- kubectl expose deployment <deployment-name> --type=NodePort --name=my-nginx (imperative way of creating service)
