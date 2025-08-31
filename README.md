# ☸️ k3s Cluster Setup

This guide documents how I deployed a lightweight Kubernetes (k3s) cluster in my homelab, with one control-plane node and multiple worker nodes.

---

## 📦 What is k3s?

"k3s is a certified Kubernetes distribution built for IoT and edge computing.  
It is lightweight, simple to install, and fully compliant with upstream Kubernetes."

k3s allows you to:
- Run a production-grade Kubernetes cluster with minimal resources
- Use the same `kubectl` tooling as standard Kubernetes
- Deploy workloads via manifests or Helm charts
- Simplify management in homelab and edge environments

🔗 Project site: [https://k3s.io/](https://k3s.io/)

---

## 💻 Hardware Used

### First Computer – HP EliteDesk 800 G1 (Control Plane)  
- **CPU:** Intel Core i5-4570  
- **RAM:** 32 GB DDR3  
- **Storage:** 480 GB SSD + 2 × 1 TB HDD (RAID1)  
- **Network:** Ethernet (static IP via Netplan)  
- **Operating System:** Ubuntu Server (main k3s host)  

### Additional Nodes  
- Lenovo T470 laptop (worker node)  
- Other desktops in homelab (planned as worker nodes)  

---

## ⏳ Installation

The cluster was installed using the official k3s installation script:

**On the control-plane node:**
```bash
curl -sfL https://get.k3s.io | sh -
sudo cat /var/lib/rancher/k3s/server/node-token
curl -sfL https://get.k3s.io | K3S_URL=https://<CONTROL-PLANE-IP>:6443 K3S_TOKEN=<TOKEN> sh -
```

---

## 🔐 Accessing the Cluster

From the control-plane node:
```bash
sudo kubectl get nodes
kubectl get pods -A
```
---

## 🚧 Status

🟢 Actively maintained as part of my [`k3s-cluster`](https://github.com/raoulmoise/k3s-cluster) project.

---
