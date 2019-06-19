# NFS Provisioner for Local Storage #

----
## Installing on a Cluster
In order to support local storage on a cluster, these files must be installed.

Because we are forcing nfs to act as local storage, we must have the deployment and provisioner on the same node that offers local storage.

To install:
1. Label that node with storage=local `kubectl label [node] storage=local`. The master node may be a suitable choice for this, since it does not run much else. 
2. On the same node, create the backing directory from which storage will be allocated. By default, this is /home/nfs-storage, but you can change this in provisioner.yaml
3. Run `kubectl create -f nfs-provisioner/`

To Use:
1. Use storage class `nfs-provisioner`