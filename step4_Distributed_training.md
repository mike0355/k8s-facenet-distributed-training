# Distributed training
In this part, we will implement distributed training in KubeFlow Pipeline. The method used is Tensorflow's MultiWorkerMirroredStrategy CPU. In this tutorial, we will learn how to specify pods to be deployed under a specific node, and how to communicate with each worker.

## Before training
Before running the training program, we need to make some settings, include:

* Adding tags to each node.
* Deploying service YAML file.
* Adding TF_config environment variables to the code.

### Adding tags to each node 
The purpose of adding tags is that the subsequent steps can directly specify the pod to be deployed under a specific node.
You run following commands to apply your node. The added screen example can shown in the **Figure.1** .
```commandline
  // add tags
  kubectl label nodes <node name>  <label name> = <value>  
  
  //show your node information
  kubectl get nodes  --show-labels=true 
```
<div align=center><img width="1000" height="100" src="https://user-images.githubusercontent.com/51089749/137849536-0bd6ad8f-f143-4eb2-8ad4-643f42cb225b.png"/></div>
<p align ="center"> <b>Figure1. Example added tags.</b></p>

### Deploying service YAML file.
When performing distributed training, worker and other workers must use the network to communicate with each other, so the pod's external port must be opened and connected to the outside through the service.
We have a [service YAML](https://github.com/mike0355/k8s-facenet-distributed-training/tree/main/pod-service) file that provides service, so you don’t need to rewrite a new file for deployment, as shown in **Figure.2** .

<div align=center><img width="500" height="500" src="https://user-images.githubusercontent.com/51089749/137850906-49510b51-9343-4d5b-83d8-d249833fcccc.png"/></div>
<p align ="center"> <b>Figure2. Example of service yaml format.</b></p>

You can run following the commands to deploy and check your service YAML file, as shown in **Figure.3**
```commandline
  //Deploy your service.yaml
  kubectl create -f <your service YAML file name>
  
  //check your service.
  kubectl get svc -n kubeflow-user-example-com
```
<div align=center><img width="1000" height="50" src="https://user-images.githubusercontent.com/51089749/137852149-fc1f2273-c39e-4739-ad33-25e20cb8bd66.png"/></div>
<p align ="center"> <b>Figure3. Example of check service.</b></p>















