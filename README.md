
# Deploy Kubernetes cluster with kubeadm

Under windows environment. Use multipass to deploy Kubernetes cluster with one control node and two worker nodes.




## Versions
* Windows 11: Windows 11 Pro 23H2 build 22631.3880
* Multipass: 1.14.0
* Kubernetes: 1.31.1
## Prepare the nodes
Multipass use Hyper-V virtual switch as NAT. The IP address will be distributed dynamically. So we need add one extra nic for static IP.

Open Hyper-v --> Virtual Switch Manager
New virtual network switch --> Internal --> Create Virtual Switch --> Name: <multipass> --> Internal network
Launch an instance with virtual switch created under the Hyper-v. You will find one additional eth1.
```console
# You can choose your preferred linux distribution. Here I used ubuntu 24.04 which use the name noble.
multipass launch noble -n controlplane -c 2 -m 4G -d 10G --network name=multipass,mode=manual
```


## Install containerd
You can follow the containerd official guide in github.

https://github.com/containerd/containerd/blob/main/docs/getting-started.md
