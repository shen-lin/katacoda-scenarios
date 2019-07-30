## Create Redis Master Controller

#### Create Replication Controller

In this example, the YAML defines a redis server called _redis-master_ using the official _redis_ running port _6379_.

The _kubectl create_ command takes a YAML definition and instructs the master to start the controller.

`kubectl create -f redis-master-controller.yaml`{{execute}}

#### What's running?

The above command created a Replication Controller. 

`kubectl get rc`{{execute}}

All containers described as Pods. A pod is a collection of containers that makes up a particular application, for example Redis. You can view this using _kubectl_

`kubectl get pods`{{execute}}

## Create Redis Service

The second part is a service. A Kubernetes service is a named load balancer that proxies traffic to one or more containers. The proxy works even if the containers are on different nodes.

Services proxy communicate within the cluster and rarely expose ports to an outside interface.

When you launch a service it looks like you cannot connect using curl or netcat unless you start it as part of Kubernetes. The recommended approach is to have a LoadBalancer service to handle external communications.

#### Create Service

The YAML defines the name of the replication controller, _redis-master_, and the ports which should be proxied.

`kubectl create -f redis-master-service.yaml`{{execute}}

#### List &amp; Describe Services

`kubectl get services`{{execute}}

`kubectl describe services redis-master`{{execute}}

## Create Redis Slave Controller

Similarly create Redis slave controller

`kubectl create -f redis-slave-controller.yaml`{{execute}}

Create Redis slave service

`kubectl create -f redis-slave-service.yaml`{{execute}}
