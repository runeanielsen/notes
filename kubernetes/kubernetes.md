# Kubernetes

Kubernetes is a software system that allows you to easily deploy and manage containerized applications on top of it. It relies on the features of Linux containers to run heterogenerous applications. 

Deploying applications through Kubernetes is always the same, whether your cluster contains only a couple of nodes or thousands of them.

Kubernetes is composed of a master node and any number of worker nodes. When the developer submits a list of apps to the master node, Kubernetes deploys them to the cluster of worker nodes.

The developer can specify that certain apps must run together and Kubernetes will deploy them on the same worker node.

Kubernetes can be thought of as an operating system for the cluster. It relieves application developers from having to implement certain infrastructure-related services into their apps; Kubernetes provides discovery, scaling, load-balancing, self-healing and leader election. 

Kubernetes will run your containerized app somewhere in the cluster, provide information to its components on how to find each other, and keep all of them running.

## Two types of nodes

A kubernetes cluster is composed of two types of nodes. 

* The master node, which hosts the Kubernetes Control Plane and controls and manages the whole Kubernetes system.

* Worker nodes that run the actual applications you deploy.

## The control plane

The control plane is what controls the cluster and makes it function. It consists of multiple components that can run on a single master node or be split across multiple nodes and replicated to ensure high availability.

* The Kubernetes API server, which you and the other Control Plane components communicate with

* The Scheduler, which schedules your apps (assigns a worker node to each deployable component of your application)

* The controller manager, which performs cluster-level functions, such as replicating components, keeping track of worker nodes, handling node failures and so on.

* etcd, a reliable distributed data store that persistently stores the cluster configuration.

## The Nodes

The worker nodes are the machines that run your containerized applications. The task of running , monitoring, and providing services to your applications is done by the following components:

* Docker, rkt, or another container runtime, which runs your containers.

* The Kubelet, which talks to the API server and manages containers on its node.

* The Kubernetes Service Proxy (kube-proxy), which load-balances network traffic between application components.

## Running an application

To run an application in Kubernetes you need to package it up into one or more container images, push those images to an image registry, and then post a description of your app to the Kubernetes API server.

The description includes

* Container image or images that contain your application components.
* How those components are related to each other.
* Which ones need to run on the same nodes and which don't. 
*For each component, you can specify how many replicas you want to run. Additionally, the description also includes which of those components provide a service to either internal or external client and should be exposed through a single IP address and made discoverable to the other components. 
* Which components that should provide a service to internal or external clients and should be exposed through a single IP address and made discoverable to other components. 

## Description

The workflow applying a description.

1. The API server processes your app's description, the Scheduler schedules the specificed groups of containers onto the available worker nodes based on the computational requirements of each group and the unallocated resources on each node at the time.

2. The Kubelet on those nodes instructs the Container Runtime to pull the required container images and run the containers.

Once the application is running, Kubernetes makes sure that the deployed state of the application always matches the description you provided. So if a node goes down then Kubernetes will redistribute the workload out to the existing nodes.

## Scaling

Kubernetes allows increasing and decreasing the number of copies, and Kubernetes will spin up additional ones or stop the excess ones. It is possible to give the job of optimizing the amount of replicas based on metrics such as CPU load and memory etc.

## Load balancing

To allow clients to find containers that provide a specific service, you tell Kubernetes which containers provide the same service and Kubernetes will expose them all though a single static IP. The kube-proxy will make sure connections to the service are load balanced across all the containers that provide the service.

The IP address of the service is always constant, even if nodes go down.


## Pods
Kubernetes do not deal with individual containers directly. Instead, it uses the concept of multiple co-located containers. The collection of containers is called a Pod.

A pod is a group of one or more tightly related containers that will always run together on the same worker node and in the same Linux namespace(s). Each pod is like a seperate logical machine with its own IP, hostname, processes, and so, running a single application.

All the containers in a pod will appear to be running on the same logical machine, whereas containers in other pods, even if they're running on the same worker node, will appear to be running on a different one.


### Access the Pod
To access a pod from the outside a service object is used. A service of type LoadBalancer is used to expose the Pod to external clients otherwise by using a CluserIp service it can only be accessed from inside the cluster. By creating a LoadBalancer type service, an external load balancer will be created and you can connect to the pod through the load balancers public ip.


## Thanks to

* [Kubernetes in Action By Marko Luksa](https://www.manning.com/books/kubernetes-in-action-second-edition?a_aid=kubiaML)
* [Getting Started with Kubernetes By Nigel Poulton](https://www.pluralsight.com/courses/getting-started-kubernetes)
