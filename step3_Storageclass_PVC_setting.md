## Storagecalss and PVC.
In this part, we need to use storageclass to implement dynamic binding. The definition of dynamic binding is to realize the action of PVC binding without editing PV by yourself, which is more efficient than editing PV to do static binding.
  
Deploy NFS provisioner.yaml on the Kubernetes. We already provided NFS provisioner.yaml file, so you only need to modify NFS server and NFS client's IP and mount directory folder location, as shown in **Figure.1**
<div align=center><img width="650" height="250" src="https://user-images.githubusercontent.com/51089749/137686605-471c8cc2-7c8f-4e62-8964-145bcdbfeb92.png"/></div>
<p align ="center"> <b>Figure1. Example of provisioner.</b></p>
  
  
After edit NFS provisioner, following this command to deploy NFS provisioner.

