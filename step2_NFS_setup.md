# Network File System Setup
 In this part, you need to install Network File System (NFS) and setup your NFS server. This is very helpful for the subsequent steps, because you can mount files to other nodes under the cluster through NFS. In this tutorial, you can use NFS to mount your persistent volume claim folder.
## Install Network File System (NFS)
Install the NFS server on your server, and install the NFS command on your client.

```commandline
//NFS Server
sudo apt-get install nfs-kernel-server

//NFS Client
sudo apt-get install nfs-common
```
On the server and client, you need to create the mount directory and give permission.

```commandline
//NFS Server
 mkdir  –p  /mnt/ (your mount directory folder name on the server)
 chmod  -R 777 /mnt/ (your mount directory folder name on the server)
 
//NFS Client
 mkdir  –p  /mnt/ (your mount directory folder name on the client)
 chmod  -R 777 /mnt/ (your mount directory folder name on the client)
```
Add the mount directory location and IP address of the client computer and server under /etc/exports path, as shown in **Figure.1**.

<div align=center><img width="650" height="250" src="https://user-images.githubusercontent.com/51089749/137679021-7b69d5c4-b504-42c6-94b5-e4257c7959ca.png"/></div>
<p align ="center"> <b>Figure1. Example of export data.</b></p>
