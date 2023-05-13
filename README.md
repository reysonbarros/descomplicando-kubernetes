# Creating cluster(kind) and pod(kubectl) with Kubernetes

## Pre-requisite: kind and kubernetes already installed.
 - https://kind.sigs.k8s.io/docs/user/quick-start/#installing-from-release-binaries
 - https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-kubectl-binary-with-curl-on-linux

### Step 1 - create cluster and nodes
kind create cluster --config kind-cluster.yaml --name giropops 

### Step 2 - create the pod based on yaml file provided
kubectl apply -f pod.yaml

### Step 3 - access the pod
kubectl exec -it giropops -- bash

### Step 4 - after access the pod execute the command to check nginx
curl localhost

![image](https://github.com/reysonbarros/descomplicando-kubernetes/assets/4474192/8476d3da-41b2-4478-b978-1de390b08f91)

### Step 5 - expose nginx service
kubectl expose pods giropops --type NodePort

### Step 6 - check what node nginx service is running(see NODE column)
kubectl get pods -o wide

![image](https://github.com/reysonbarros/descomplicando-kubernetes/assets/4474192/df147587-197a-493a-8727-8d8cb6d1cf77)


### Step 7 - check the column INTERNAL-IP from node
kubectl get nodes -o wide

![image](https://github.com/reysonbarros/descomplicando-kubernetes/assets/4474192/b4aa12b9-d917-4957-bb77-804a7da08145)

## Step 8  - verify what port the nginx service is running by host side
kubectl get services

![image](https://github.com/reysonbarros/descomplicando-kubernetes/assets/4474192/6dc0c787-6ce9-45ce-80a4-d97bb33b6512)


![image](https://github.com/reysonbarros/descomplicando-kubernetes/assets/4474192/a7592cd4-6967-4666-8b39-c4fe147ae879)
