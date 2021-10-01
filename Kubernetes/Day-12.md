<div align="center">
  <h1> Architecture of Kubernetes Cluster </h1>
</div>

A **Kubernetes cluster** consists of a set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node. <br>

![K8s_cluster](https://github.com/Vrukshali-26/DevOps/blob/main/images/K8s_cluster.png)
<br>

## Control Plane
The control plane manages the worker nodes and the Pods in the cluster. <br>

## Control Plane Components

### kube-apiserver
The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. <br>
The API server is the front end for the Kubernetes control plane. <br>
The main implementation of a Kubernetes API server is kube-apiserver. <br>
kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. <br>
You can run several instances of kube-apiserver and balance traffic between those instances. <br>

### etcd
Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data. <br>
If your Kubernetes cluster uses etcd as its backing store, make sure you have a back up plan for those data. <br>

### kube-scheduler
Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on. <br>
Factors taken into account for scheduling decisions include: individual and collective resource requirements, hardware/software/policy constraints, affinity and anti-affinity specifications, data locality, inter-workload interference, and deadlines. <br>

### kube-controller-manager
Control plane component that runs controller processes. <br>
Logically, each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process. <br>


### cloud-controller-manager
A Kubernetes control plane component that embeds cloud-specific control logic. The cloud controller manager lets you link your cluster into your cloud provider's API, and separates out the components that interact with that cloud platform from components that only interact with your cluster. <br>
The cloud-controller-manager only runs controllers that are specific to your cloud provider. If you are running Kubernetes on your own premises, or in a learning environment inside your own PC, the cluster does not have a cloud controller manager. <br>

As with the kube-controller-manager, the cloud-controller-manager combines several logically independent control loops into a single binary that you run as a single process. You can scale horizontally (run more than one copy) to improve performance or to help tolerate failures. <br>


## Node Components

### kubelet
An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod. <br>
The kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy.  <br>
The kubelet doesn't manage containers which were not created by Kubernetes. <br>

### kube-proxy
kube-proxy is a network proxy that runs on each node in your cluster, implementing part of the Kubernetes Service concept. <br>
kube-proxy maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster. <br>
kube-proxy uses the operating system packet filtering layer if there is one and it's available. Otherwise, kube-proxy forwards the traffic itself. <br>


## Addons
Addons use Kubernetes resources (DaemonSet, Deployment, etc) to implement cluster features. Because these are providing cluster-level features, namespaced resources for addons belong within the kube-system namespace. <br>
Selected addons are described below; for an extended list of available addons, please see Addons. <br>

