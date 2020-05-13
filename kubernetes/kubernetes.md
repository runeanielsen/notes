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


## Running an application in Kubernetes
To run an application in Kubernetes you need to package it up into one or more container images, push those images to an image registry, and then post a description of your app to the Kubernetes API server.

The description includes

* Container image or images that contain your application components.
* How those components are related to each other.
* Which ones need to run on the same nodes and which don't. 
*For each component, you can specify how many replicas you want to run. Additionally, the description also includes which of those components provide a service to either internal or external client and should be exposed through a single IP address and made discoverable to the other components. 













