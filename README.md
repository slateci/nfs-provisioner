# NFS Provisioner for Local Storage #

----
## Installing on a Cluster
In order to support local storage on a cluster, these files must be installed.

Because we are forcing nfs to act as local storage, we must have the deployment and provisioner on the same node that offers local storage.

To install:
1. Label that node with storage=local `kubectl label [node] storage=local`
2. Ensure you have a `slate-core` namespace. If you don't, run `kubectl create namespace slate-core`
2. Run `kubectl create -f nfs-provisioner/ --namespace slate-core`

To Use:
1. Use storage class `nfs-provisioner`
2. Use node selector for local storage in deployment  
```
...
nodeSelector:
        storage: "local"
...
```
