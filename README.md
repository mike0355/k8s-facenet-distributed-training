# Distributed training with Kubeflow pipeline
<font size=4>This example demonstrates how to use kubeflow end-to-end to use Tensorflow MuiltiWorkerMirroredStrategy on the local k8s cluster for distributed training, and implement image similarity calculation through FaceNet algorithm and OpenCV face recognition technology.</font>
# Goals
<font size=4> This tutorial will implement the following items:  
  
*	Use Tensorflow MuiltiWorkerMirroredStrategy to demonstrate distributed training .  
*	Use FaceNet algorithm and OpenCV to implement image similarity calculation .  
  
<font size=4> At the end of this tutorial, you will learn how to :  
*  Create a new cluster and deploy the Kubeflow on Kubernetes .
*  Install and setup NFS(Network File System) to mount your volume . 
*  Deploy storageclass and pvc to implement dynamic binding .
 
*  Use Kubeflow Pipeline and Tensorflow CPU to train a distributed model on the cluster .  
*  Use flask server and web UI to implement model serving .
