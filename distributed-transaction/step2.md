Create PersistentVolume and PCV for two MariaDB hosts.

`kubectl create -f mariadb1-pv.yaml`{{execute}}

`kubectl create -f mariadb2-pv.yaml`{{execute}}

Verify the PVs and PVCs are created.

`kubectl get pv`{{execute}}

`kubectl get pvc`{{execute}}

Create two MariaDB instances.

`kubectl create -f mariadb1-deployment.yaml`{{execute}}

`kubectl create -f mariadb2-deployment.yaml`{{execute}}

Verify that both MariaDB pods are running before next step.

`kubectl get pods`{{execute}}

`kubectl get services`{{execute}}