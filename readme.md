# Kubernetes The Hard Way (ESXI with centos 7)

This tutorial walks you through setting up Kubernetes the hard way. I am going to use with Vmware ESXI and Centos7 for this lab. Feel free to use this K8s lab for your reference. 


## Lab Details

### Infra 
| Name  | IP Address | Role
---     | ---        | --- 
Fortigate | 174.30.10.1 | DHCP and Policy
Esxi    | 174.30.10.100 | ESXI

# Network 
Network / IP	| Description
--- | ---
174.30.10.0/24  | Vlan 10 (Management Lan)
174.30.20.0/24	| Vlan 20 (Server Lan)
10.98.100.0/22	| k8s Pod network
10.98.96.0/24	| k8s Service network
10.98.95.18	| k8s API server (external IP - haproxy)
10.98.96.1	| k8s API server (internal IP)
10.98.96.10	| k8s DNS

## Server Cluster Details

|   Name    |   IP Address | Role
| ---   | ---   | ---
PXE-DNS | 174.30.20.100 | PXE and DNS 
K8s-Controller1 | 174.30.20.101 | Controller 1
K8s-Controller2 | 174.30.20.102 | Controller 2
K8s-Controller3 | 174.30.20.103 | Controller 3
K8s-Worker1 | 174.30.20.104 | Worker 1
K8s-Worker2 | 174.30.20.105 | Worker 2
K8s-Worker3 | 174.30.20.106 | Worker 3
HAProxy | 174.30.20.107 | Load Balancer
NFS     | 174.30.20.109 | NFS Server

## K8s Version

- kubernetes v1.0.0
- crictl v1.0.0-beta.0
- containerd v1.4.4
- coredns v1.8.3
- cni v0.9.1
- etcd v3.4.15

# Steps

1. Infrastructure Setup
2. PXE And DNS Setup
3. Install the Client Tools
4. Creating Certificate for K8s
5. Generate Kubernetes Config file 
6. Generate Data Encrypted Config file
7. Bootstrapping ETCD
8. Config Load Balancer (HA Proxy)
9. Bootstrapping Control Plane
10. Bootstrapping Worker Nodes
11. Config Admin kubectl

# Referencing 

- [Kubernetes The Hard Way (kelseyhightower)](https://github.com/kelseyhightower/kubernetes-the-hard-way/tree/master)

- [Kubernetes The Hard Way (Defo)](https://github.com/defo89/kubernetes-the-hard-way-lab)