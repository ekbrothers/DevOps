
# Quicklinks
* [Kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* [Kubectl Commands](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)
* [Kubernetes Glossary](https://kubernetes.io/docs/reference/glossary/?fundamental=true)
* [Play with Kubernetes Classroom](https://training.play-with-kubernetes.com/kubernetes-workshop/)
* [Understanding Kubernetes Objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/)


---

**Kubernetes** is an open-source system for automating deployment, scaling, and management of containerized applications. It groups containers that make up an application into logical units for easy management and discovery. Kubernetes builds upon 15 years of experience with running production workloads at Google.

---

Kubernetes supports Docker and rkt and consists of **Pods**, **Replication Controllers**, **Replica Sets**, **Services**, and **Deployments**. It has advanced features such as interfacing with external load balancer providers (such as Microsoft Azure Load Balancer), auto-scaling, and self-healing.



# Kubernetes Up and Running

`minikube start`
`kubectl config view`

# Main Components of Kubernetes Instance
* [**Masters**](https://github.com/ekbrothers/DevOps/wiki/Kubernetes#masters)
* [**Nodes**](https://github.com/ekbrothers/DevOps/wiki/Kubernetes#nodes)
    * A node is a worker machine in Kubernetes.

## Masters
kube-apiserver
* Exposes restful API
* Consumes JSON
* Front-end to control plane

Cluster Store
* Persistent storage
* cluster state and config lives here
* usees [etcd](https://etcd.io/)
     * Distributed, consistent, watchable
     * **source of truck for cluster**

kube-controller-manager
* Controller of controllers
    * Node controller
    *  Endpoints controller
    * Namespace controller

kube-scheduler
Watches apiserver for new pods

## Nodes
### Kubelet
* main kubernetes agent
* registers node with cluster
* watches apiserver
* instantiates pods
* Reports back to master
* exposes endpoint on :10255
* /spec
     * /spec
     * /healthz
     * /pods

### Container Engine
* Does container engine
    * pulling images
    * starting/stopping containers
* Pluggable
    * Usually Docker
    * Can be rkt

### kube-proxy
    * Pod IP addresses
         * All containers in a pod share a single IP
    * Load balances across all pods in a service

Declarative Model & Desired State
* Kubernetes operates on a declarative model
* described by *.YAML or *.JSON 

## Objects in the Kubernetes API
* Pods
* Replication Controllers
* Deployments
* Services
Containers always run inside of pods
Pods can have multiple containers

Pod
* ring-fenced environment
* kernel-namespaces
* All containers in pod share the pod environment
    * If use case where multiple containers need to share same 

Unit of scaling is pods.

Pods are Atomic
Pods are Mortal
* Pending
* Running
* Succeeded/Failed

## Services
* IP Churn
* Service objects sits in front of pods and load balances for other pods at same IP and DNS
* A pod belongs to a service is via *labels*
    * Everything gets labels
    * Services determine which pods to load balance via labels
    * Services only send traffic to healthy pods
    * Can be configured for session affinity in *.YAML file
    * Can point to things outside the cluster
    * Random load balancing
    * Uses TCP by default

## Deploying Pods
* usually via higher level objects
* is possible to deploy via pod manifest file (*.YAML)
* Also by Replication Controller

Deployments are all about declaritiveness
Best way to run work production environments

# Working with Pods
Pods are the atomic unit of scheduling
A pod contains 1 or more containers
You deploy a pod to a cluster by defining it in a manifest file
Manifest file is fed into apiserver.
Regardless of how many containers in a pod, each pod only gets a single IP.
Each container in the same pod shares the same namespace, etc.
Every pod can talk directly to ever other pod
Intrapod location - 2 containers can not use same IP


* [Create Static Pods](https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/)

* **Replica Set** is the next-generation Replication Controller.<br>**ReplicaSet**, like **ReplicationController**, ensures that a specified number of pods replicas are running at one time. 
<br>ReplicaSet supports the new set-based selector requirements as described in the labels user guide, whereas a Replication Controller only supports equality-based selector requirements.

* Reconciliation loop

# Pod Manifest (YAML) Files
* [Understanding Kubernetes Objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/)