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
# The FaceNet and the Model training
  In this tutorial, a method called FaceNet is used to implement a face recognition on K8s. FaceNet presents a method to train the features of Euclidean as a similarity between two face images, and output the distance as the similarity between two face images. In addition, we use triplet loss function to optimized the model.  
  Before training our data, three components are selected as triplets, as shown in **Figure1**, which include an anchor, a positive and a negative from the dataset. Since the model is trained in the Euclidean space, we assume that the distance between two points directly corresponds to the similarity between the two face images. As shown in **Figure2**. after training the model,the distance between the anchor and the positive will be reduced, and that between the anchor and the negative will be increased .

  
  
<center>
![image](https://user-images.githubusercontent.com/51089749/137067151-cf04c6cf-4597-477b-b48d-9948c1e4ff99.png)
</center>
  
  
  
![image](https://user-images.githubusercontent.com/51089749/137064990-37c1fbe4-bdb0-40e1-a285-360bc97e5a51.png)


