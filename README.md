# Redis Kubernetes Test

* Sample project to test out running jobs in parallel via Redis message queue and Kubernetes async workers
* Followed [this tutorial on Kubernetes docs](https://kubernetes.io/docs/tasks/job/fine-parallel-processing-work-queue/)
  * Command to start redis pod: `kubectl run -i --tty temp --image redis --command "/bin/sh"` in this stupid fucking tutorial doesn't even work; got it working by using a YAML file to configure and start pod:
    * Create basic YAML file called `redis-pod.yaml`
    * `kubectl apply -f redis-pod.yaml`
    * `kubectl exec -it redis-pod -- /bin/sh`
    * `redis-cli -h redis-pod`

## Kubernetes Terminology
Kubernetes is a bit much on first glance, let's define some terms so that we can understand it better:
* Nodes: physical or virtual machine in cluster; worker
  * Consist of 3 components:
    * Kubelet: ensures that each container is running in a pod
    * Container runtime: 
    * Kube-proxy: maintains network rules for communication across pods
  * Managed by a single control plane
  * Contain multiple pods
* Control plane: component that manages the entire Kubernetes cluster 
  * Consist of 4 components:
    * API server
    * Scheduler
    * Controller manager
    * etcd
* Deployment: file that specifies how to deploy a cluster
* Service: ???
* Pod: single instance of a running process; can have multiple containers
* Container: isolated and lightweight unit of software that can run an application (its binary, dependencies, runtime, settings) in its own environment, regardless of its VM's or instance's OS
  * Container image: ready-to-run software package/binary for an application (e.g. Redis, Postgres)

### Useful Commands
* `kubectl get pods`
* `docker ps`
* `kubectl get svc`
* `kubectl get deployments`
* `minikube start`
