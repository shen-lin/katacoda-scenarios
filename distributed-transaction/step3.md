Start webapp replica set

`kubectl create -f frontend-service.yaml`{{execute}}

`kubectl create -f frontend-controller.yaml`{{execute}}

Verify that webapp pods are running.

`kubectl get pods`{{execute}}

Look for the dynamic port number on the host for webapps
`kubectl get services`{{execute}}

Click Dashboard tab and enter the port number above to start web app.