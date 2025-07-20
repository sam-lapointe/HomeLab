# HomeLab
This repository documents the setup of my personal home lab, built for learning, testing, and running self-hosted applications in a Kubernetes environment.

## Infrastructure Overview
The home lab consists of the following hardware:

- **1 Proxmox Server**  
    Hosts virtual machines, including the Kubernetes control plane.

- **2 Mini PCs** running Ubuntu Server  
    Serve as Kubernetes worker nodes.

- **Pfsense Router**  
    Manages firewall rules, VLANs, and routing.

- **Netgear Managed Switch**  
    Handles VLAN segmentation and network traffic between devices.

### Network Architecture
The home network is segmented using **VLANs**. All Kubernetes nodes are placed in the DMZ VLAN, as they are intended to host publicly accessible services. Additional VLANs isolate infrastructure services and client devices.

## Kubernetes Cluster
Kubernetes is deployed **on-premises** using the following components:

- **kubeadm** - for cluster initialization and management
- **containerd** - as the container runtime
- **calico** - as the Container Network Interface (CNI) plugin.

The Kubernetes **control plane** runs on a **Ubuntu Server VM** hosted on Proxmox, while the two mini PCs act as **worker nodes**.

### Applications Configuration and Deployment
Most applications are configured and deployed using **ArgoCD**. Configuration files are version-controlled in this repository, and ArgoCD automatically applies changes to the Kubernetes cluster when updates are committed.

ArgoCD was initially deployed manually by following the official documentation, and it now manages the continuous deployment pipeline for the cluster.
