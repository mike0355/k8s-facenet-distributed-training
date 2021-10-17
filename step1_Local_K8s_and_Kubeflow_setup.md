# Create a new cluster on local Kubernetes

<font size=4> In this section, we need to install Kubernetes and create a new cluster step by step.</font>

## Create cluster and muilti nodes
<font size=4> At the first, we need add ip address and user name of the master node and other nodes under the specified path, As shown in **Figure.1**</font>
```commandline
   cd /etc/hosts
```
<div align=center><img width="650" height="250" src="https://user-images.githubusercontent.com/51089749/137610994-d6b18ae9-e156-49c3-af0b-1ec9f2aed22e.png"/></div>
<p align ="center"> <b>Figure1. Example of specified path.</b></p>

## Install docker
<font size=4>You can run this command to install docker.</font>
```commandline
  sudo apt install docker.io -y
```
<font size=4>If you want to let your docker to start automatically when your computer is turned on, you can run the following command.</font>
```commandline
  sudo systemctl start docker
  sudo systemctl enable docker
```
## Disable SWAP
<font size=4>Run the following command to disable swap. </font>
```commandline
  sudo swapon -s
  sudo swapoff -a
```
## Install kubeadm, kubelet and kubectl
 Now start to install the necessary packages for kubernetes.
```commandline
  sudo apt-get update
  sudo apt-get install -y apt-transport-https ca-certificates curl
```
 Download the Google Cloud public signing key.
```commandline
  sudo curl -fsSLo/usr/share/keyrings/kubernetes-archive-keyring.gpghttps://packages.cloud.google.com/apt/doc/apt-key.gpg
```
 Add the Kubernetes apt repository.
```commandline
  echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
Update packages and install kubeadm, kubelet, kubectl.
```commandline
  sudo apt-get update
  sudo apt-get install -y kubelet kubeadm kubectl 
  sudo apt-mark hold kubelet kubeadm kubectl
```
The above commands will automatically install the latest version for you, if you want to install the specified version, run the following commands.
```commandline
  sudo apt-get install -y kubelet= <Specified kubelet version>
  sudo apt-get install -y kubeadm= <Specified kubeadm version>
  sudo apt-get install -y kubectl= <Specified kubectl version>
```
Run this command to deploy your master node, and you will get some messages as **Figure.2** .
```commandline
  sudo kubeadm init --pod-network-cidr=10.244.10.0/16--apiserver-advertise-address= <Your master node IP address>
```
<div align=center><img width="650" height="250" src="https://user-images.githubusercontent.com/51089749/137614179-3c7f6ba5-edd5-4c22-ad6e-7b1bf77fb3ed.png"/></div>
<p align ="center"> <b>Figure2. Example of deployment master node.</b></p>

Create .kube folder, this setting is to allow general users to use kubectl.
```commandline
  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
After deploy master node, and then you need to deploy the pod-network to the cluster.
```commandline
  kubectl apply -fhttps://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```
Finally, you can use the **Figure.2** redframe's command to join any number of worker nodes by running the following on each as root. At this step, your multi nodes cluster is established.
