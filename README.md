
# Deploy Kubernetes cluster with multipass and kubeadm

kubeadm named as the best practice for deploying the K8S cluster. I choose multipass as it's quite easy to create VMs on your local host.


## Versions
* Windows 11: Windows 11 Pro 23H2 build 22631.3880
* Multipass: 1.14.0
* Kubernetes: 1.31.1
* OS: Ubuntu 24.04 LTS

## Prepare the nodes with multipass
In my case, i use multipass with Hyper-V.

- Step 1: Create an internal network named "multipass"
- Step 2: Launch an instance with virtual switch created under the Hyper-v. You will find one additional eth1.
    ```console
    # You can choose your preferred linux distribution. Here I used Ubuntu 24.04 LTS with the name noble.
    multipass launch noble -n controlplane -c 2 -m 4G -d 10G --network name=multipass,mode=manual --cloud-init cloud-init.yaml
    ```


## Install containerd
You can follow the containerd official guide in github.

https://github.com/containerd/containerd/blob/main/docs/getting-started.md
