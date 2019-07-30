Start webapp replica set

`kubectl create -f frontend-service.yaml`{{execute}}

`kubectl create -f frontend-controller.yaml`{{execute}}

Verify that webapp pods are running.

`kubectl get pods`{{execute}}

`kubectl get services`{{execute}}