# Kubernetes Notes

a tool for running a bunch of containers.

node: a vm that runs some number of containers.

pod != container, pod can run multiple containers.
service handles networking between nodes etc.
deployment monitors a set of pods and make sure they are running and restart when they crash.

Creating a deployment:
You need:
* to specify the container image for your application.
* number of replicas you want to run.

Services
type of services => cluster ip, node port, load balancer, external name
cluster ip - set up a url to access a pod, only exposes pods in the cluster
load balancer - make pod accessible from outside of the cluster.
node port - for dev purpose only.

for traffic towards deployment: outside world <=> ingress controller <=> cluster

for access to ingress nginx server: /etc/hosts, 127.0.0.1 domain name

Commands:
`kubectl get deployments` - list all deployments
`kubectl describe deployment [depl name]`
`kubectl delete deployment [depl name]` - delete a deployment
`kubectl get pods` - get all the running pods
`kubectl exec -it <pod name> <cmd>`
`kubectl logs <pod name>`
`kubectl delete pod <pod name>`
`kubectl describe pod <pod name>`
`kubectl rollout restart deployment [depl-name` - restart deployments
`kubectl get services` - you can check out nodeport services from here
`kubectl describe service <service name>`
`kubectl cluster-info` - view cluster detail
`kubectl get nodes` - nodes that can be used to host applications
`kubectl get deployments` - get deployments
`kubectl create deployment <deployment name> -- <image src>:<version>` - create a deployment
`kubectl proxy` - the kubectl command can create a proxy that will forward communications into the cluster-wide, private network
