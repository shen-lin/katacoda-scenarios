## Create Redis Master Controller and Service

#### Create Redis Maseter Controller

`kubectl create -f redis-master-controller.yaml`{{execute}}

#### Create Redis Master Service

`kubectl create -f redis-master-service.yaml`{{execute}}


## Create Redis Slave Controller and Service

Similarly create Redis slave controller

`kubectl create -f redis-slave-controller.yaml`{{execute}}

Create Redis slave service

`kubectl create -f redis-slave-service.yaml`{{execute}}


#### Verify Redis master-slave cluster is starrted. Make sure all the pods have STATUS 'Running' before going to next step.

`kubectl get rc`{{execute}}

`kubectl get services`{{execute}}

`kubectl describe services redis-master`{{execute}}

`kubectl get pods`{{execute}}