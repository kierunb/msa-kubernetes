# .NET Microservices with Kubernetes experiments

## > docker compose

```shell
docker compose build
docker compose up
docker compose down
```

## > kubectl commands

- [kubectl cheat sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

```shell
# general info
kubectl cluster-info
kubectl version
kubectl describe pods <pod name>

#kubeconfig location
cat $HOME\.kube\config

# list nodes (no)
kubectl get node -o wide
kubectl top node 

# scale nodes manually
az aks scale --resource-group myResourceGroup --name myAKSCluster --node-count 3

# list everything
kubectl get all --all-namespaces

# pods (po)
kubectl get pods --watch
kubectl logs my-pod                                 # dump pod logs (stdout)
kubectl logs -l name=myLabel
kubectl attach my-pod -i                            # Attach to Running Container
kubectl port-forward my-pod 5000:6000 
kubectl top pod POD_NAME --containers               # Show metrics for a given pod and its containers

# run pod with attached shell, dispose after exit
kubectl run -i --rm --tty busybox --image=busybox -- sh

# generate specs
kubectl run nginx --image=nginx --dry-run=client -o yaml > pod.yaml

# namespaces
kubectl get namespaces (ns)
kubectl get pods –n mynamespace

# create, manage, delete objects/configuration
kubectl create -f <file/folder/url>
kubectl apply -f <file/folder/url>
kubectl delete -f <file/folder/url>

# deployments (deploy)
kubectl get deployment
kubectl scale --replicas=5 deployment/backend-deployment

# upgrade deployment
kubectl set image deployment backend-deployment backend-deployment=<acrLoginServer>/backend-deployment:v2

# scale deployment
# install metric server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.6.1/components.yaml
# hpa
kubectl autoscale deployment backend-deployment --cpu-percent=50 --min=1 --max=6

# generate load test
https://docs.microsoft.com/en-us/learn/modules/aks-workshop/10-scale-application

```
