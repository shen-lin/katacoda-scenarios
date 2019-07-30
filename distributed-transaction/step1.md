Wait for the folder created. Then enter the following folder that contains the Kubernetes config files.

`cd /root/tutorial/distributed-transaction/kubernetes-config`{{execute}}

Replace the NFS server IP address with the host IP of the current Katacoda session. Wait for the completion of this step.

`ip=$(ifconfig ens3 2>/dev/null|awk '/inet addr:/ {print $2}'|sed 's/addr://');`{{execute}}
`sed -i "s/KATACODA-DYNAMIC-IP/${ip}/g" mariadb1-pv.yaml`{{execute}}
`sed -i "s/KATACODA-DYNAMIC-IP/${ip}/g" mariadb2-pv.yaml`{{execute}}

Verify the cluster has been started by running launch.sh

`kubectl cluster-info`{{execute}}

Deploy NFS Server

`docker run -d --net=host \
   --privileged --name nfs-server \
   katacoda/contained-nfs-server:centos7 \
   /exports/data-0001 /exports/data-0002`{{execute}}