## Storagecalss and PVC.
In this part, we need to use storageclass to implement dynamic binding. The definition of dynamic binding is to realize the action of PVC binding without editing PV by yourself, which is more efficient than editing PV to do static binding.
  
Step1: Deploy NFS provisioner.yaml on the Kubernetes. We provide NFS provisioner.yaml file, so you only need to modify NFS server and NFS client's ip and mount directory folder location, as shown in **Figure.1**


![image](https://user-images.githubusercontent.com/51089749/137686605-471c8cc2-7c8f-4e62-8964-145bcdbfeb92.png)
