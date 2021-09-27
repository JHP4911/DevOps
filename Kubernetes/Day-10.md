# Persistent volumes (PV) and Claims (PVC) in Kubernetes





### Persistent Volumes

A PersistentVolume (PV) is a storage resource in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes

![PV_PVC](https://github.com/Vrukshali-26/DevOps/blob/main/images/pv-pvc-1.png)

### Official Documentation : https://kubernetes.io/docs/concepts/storage/persistent-volumes/

### Persistent Volume Claim

A persistent volume claim (PVC) is a request for storage by a user from a PV. Claims can request specific size and access modes.  (e.g: they can be mounted once read/write or many times read-only).

![PVC](https://github.com/Vrukshali-26/DevOps/blob/main/images/pv-pvc-2.JPG)

### Access Modes :

1. ReadWriteOnce: The Volume can be mounted as a read-write by a single node.
2. ReadOnlyMany: The Volume can be mounted read-only by many nodes.
3. ReadWriteMany: The Volume can be mounted as a read-write by many nodes.

### Configure a Pod to Use a PersistentVolume for Storage
Official Documentation : https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/

### Various Examples Explained :
Blog Link : https://medium.com/avmconsulting-blog/persistent-volumes-pv-and-claims-pvc-in-kubernetes-bd76923a61f6



