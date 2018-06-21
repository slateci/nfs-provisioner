# NFS Provisioner for Local Storage #

----
## Installing on a Cluster
In order to support local storage on a cluster, these files must be installed.

Because we are forcing nfs to act as local storage, we must have the deployment and provisioner on the same node that offers local storage.

To install:
1. Create a directory on the node that will be offering local storage at path /node-storage
2. Label that node with storage=local `kubectl label [node] storage=local`
3. Install the cluster role, and cluster role binding permissions to slate-core namespace on cluster
4. Install the service account, and storage class to slate-core namespace on cluster
5. Install the deployment to slate-core namespace on cluster

To Use:
1. Use storage class `nfs-provisioner`
2. Use node selector for local storage in deployment  
```
...
nodeSelector:
        storage: "local"
...
```
