# `kubectl` Cheat Sheet

## General
- **Get help:** `kubectl help`
- **Version info for kubectl and cluster:** `kubectl version`
- **View the kubectl configuration:** `kubectl config view`

## Cluster Information
- **Display addresses of the master and services:** `kubectl cluster-info`
- **List all nodes in the cluster:** `kubectl get nodes`

## Configuration
- **Set which Kubernetes cluster `kubectl` communicates with:** `kubectl config use-context my-cluster`
- **View kubeconfig settings:** `kubectl config view`
- **Create a new kubeconfig for a service account:** `kubectl create serviceaccount my-service-account`

## Working with Kubernetes Objects
- **List resources:** `kubectl get <resource>`
- **Create resource(s):** `kubectl create -f <file>`
- **Apply changes to a resource:** `kubectl apply -f <file>`
- **Delete resource(s):** `kubectl delete -f <file>`
- **Display the detailed state of one or more resources:** `kubectl describe <resource>/<name>`
- **Edit and update the definition of one or more resources on the server:** `kubectl edit <resource>/<name>`

## Pods and Containers
- **List all pods:** `kubectl get pods`
  - Add to monitor the changes `--watch`
  - Add to see more details `-o wide`
  - Add to see a full copy of the pod `-o yaml`
- **List all pods in all namespaces:** `kubectl get pods --all-namespaces`
(add --watch to monitor the changes)
- **List pods in a specific namespace:** `kubectl get pods -n my-namespace`
- **Get detailed information about a specific pod:** `kubectl describe pod my-pod`
- **Run a command in a new container in a pod:** `kubectl run my-pod --image=my-container`
- **Get logs from a container in a pod:** `kubectl logs my-pod`
   - add `-c <container-name>` to get logs from a non primary container
- **Execute a command in an existing container in a pod:** `kubectl exec my-pod -- ls /`

## Deployments
- **Create a deployment:** `kubectl create deployment my-dep --image=my-image`
- **Get deployments:** `kubectl get deployments`
- **Edit a deployment:** `kubectl edit deployment/my-dep`
- **Scale a deployment:** `kubectl scale deployment my-dep --replicas=5`
- **Roll out an update to a deployment:** `kubectl set image deployment/my-dep my-container=my-image:v2`
- **Rollback a deployment:** `kubectl rollout undo deployment/my-dep`
- **View the rollout history of a deployment:** `kubectl rollout history deployment/my-dep`

## Services
- **Expose a pod as a service:** `kubectl expose pod my-pod --port=444 --name=my-service`
- **Get services:** `kubectl get services`
- **Delete a service:** `kubectl delete service my-service`

## Labels and Selectors
- **Label a resource:** `kubectl label <resource> key=value`
- **List resources with a specific label:** `kubectl get <resource> -l key=value`

## Namespaces
- **Create a new namespace:** `kubectl create namespace my-ns`
- **Get resources in a namespace:** `kubectl get <resource> -n my-ns`
- **Set the default namespace for current context:** `kubectl config set-context --current --namespace=my-ns`

## Contexts
- **Get current context:** `kubectl config current-context`
- **List all contexts:** `kubectl config get-contexts`
- **Switch to another context:** `kubectl config use-context my-context`

## Miscellaneous
- **Port forward to a local port:** `kubectl port-forward <pod-name> <local-port>:<pod-port>`
  - `kubectl port-forward svc/<service-name> <local-port>:<pod-port> -n <namespace>`
- **Copy files from/to a container:** `kubectl cp <pod-name>:/path/to/remote/file /path/to/local/file`
- **Watch resources continuously:** `kubectl get <resource> --watch`

Remember to replace placeholders (like `<resource>`, `<name>`, `<file>`, etc.) with actual values corresponding to your Kubernetes objects.
