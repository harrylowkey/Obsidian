#k8s 

Testing: minikube
Template: Helm chart
# Infrastructures

![Traffic flows](Untitled.heic)

![Object types](Untitled%201.heic)

## Components

When you deploy Kubernetes, you get a **cluster**.

A Kubernetes cluster consists of a set of worker machines, called [nodes](https://kubernetes.io/docs/concepts/architecture/nodes/), that run containerized applications. Every cluster has at least one worker node.

The worker node(s) host the [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) that are the components of the application workload. The [control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) manages the worker nodes and the Pods in the cluster. In production environments, the control plane usually runs across multiple computers and a cluster usually runs multiple nodes, providing fault-tolerance and high availability.

![[k8s cluster.png]]

## Control Plane Components 
- kube-apiserver
- etcd
- kube-scheduler
- kube-controller-manager
- cloud-controller-manager

## Node Components
- kubelet
- kube-proxy
- container runtime