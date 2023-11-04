# KinD (Kubernetes in Docker) Cheat Sheet

## Installation
- **Install KinD:** Refer to the official [KinD documentation](https://kind.sigs.k8s.io/docs/user/quick-start/#installation) for installation instructions.

## Cluster Management
- **Create a Cluster:** `kind create cluster --name <cluster-name>`
- **Delete a Cluster:** `kind delete cluster --name <cluster-name>`
- **Get Clusters:** `kind get clusters`
- **List Nodes:** `kind get nodes --name <cluster-name>`
- **Export Kubeconfig:** `kind get kubeconfig --name <cluster-name> > kubeconfig.yaml`

## Node Management
- **Add a Node to Cluster:** `kind create node --name <node-name> --cluster <cluster-name>`
- **Delete a Node:** `kind delete node --name <node-name>`

## Cluster Configuration
- **Create Cluster with Config:** `kind create cluster --name <cluster-name> --config config.yaml`
  - Config can include settings for multiple nodes, networking, kubeadm config, etc.

## Advanced Usage
- **Create Multi-Node Cluster:**
  ```yaml
  kind: Cluster
  apiVersion: kind.x-k8s.io/v1alpha4
  nodes:
  - role: control-plane
  - role: control-plane
  - role: worker
  - role: worker
