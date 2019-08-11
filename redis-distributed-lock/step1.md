Go to the folder that contains all the kubernetes configuration file for this scenario. Do not execute the following step until this command succeeds.

`cd /root/tutorial/redis-distributed-lock/kubernetes-config`{{execute}}

Starting kubernetes cluster.

`launch.sh`{{execute}}

Verify the cluster has been started by running launch.sh

`kubectl cluster-info`{{execute}}

List the nodes in the cluster

`kubectl get node`{{execute}}