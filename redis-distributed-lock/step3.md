Launch Frontend Controller and Service

`kubectl create -f frontend-controller.yaml`{{execute}}

`kubectl create -f frontend-service.yaml`{{execute}}

List controllers and pods. Make sure the frontend pods are all having STATUS 'Running'.

`kubectl get rc`{{execute}}

`kubectl get services`{{execute}}

`kubectl get pods`{{execute}}

