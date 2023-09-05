# kubernetes-cheatsheet

## Pods 
The smallest unit of K8s 

Example pod yaml:
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx 
```

Useful commands:
```
-- create pod
kubectl create -f <file_name>.yaml

-- get all pods
 kubectl get pods --all-namespaces

-- get pods with namespace
kubectl get pods --namespace={namespace}

-- view pod logs
kubectl logs <pod_name> --namespace {namespace}
kubectl logs <pod_name> --namespace {namespace}
kubectl logs <pod_name> --namespace kube-system

-- delete single pod
kubectl delete pod <pod_name>

-- to create a pod with nginx image
kubectl run nginx --image=nginx

-- describe all pod details
kubectl describe pods

-- extract the definition to a file
kubectl get pod <pod_name> -o yaml > pod-definition.yaml

-- edit pod properties
kubectl edit pod <pod_name>

-- describe one specific pod detail
kubectl describe pods <pod_name>
```

---

## Replication Controllers and Replica Sets
Role of replica sets: Monitor pods and if any fail, deploy new pods to replace them.
Labelling of pods help replica sets identify which pods it should monitor.
Main difference between them is selectors. Replica Sets can manage pods that was created before it.

Useful commands:
```
kubectl create -f <filename>
kubectl get replicaset
kubectl edit replicaset <replicaset_name>
kubectl delete replicaset myapp-replicaset
kubectl replace -f <filename>
kubectl scale --replicas=6 -f <filename>
kubectl describe rs
But scale command does not persist or change the replicas that was initialized in the file itself.
```

## Deployments
Deployments and ReplicaSet is similar, except that deployments create new kubernetes object deployment.

Useful commands:
```
kubectl create -f <filename>
kubectl describe deployment <name>
kubectl get deployments --namespace=<namespace>
kubectl get replicaset
kubectl get pods
kubectl get all

kubectl rollout status deployment/<deployment_name>
kubectl rollout history deployment/<deployment_name>
kubectl rollout undo deployment/<deployment_name>
```

## Services

Useful commands:
```
kubectl get services
```

Other commands:
```
kubectl get svc
kubectl get ingress

-- delete everything in a certain namespace
kubectl delete all --all -n {namespace}

-- get kubernetes secrets
kubectl get secrets

-- to retrieve secret variable
kubectl get secret <your_secret_name> -o jsonpath='{.data}'
-- decode variable
echo '<your_string_here>' | base64 --decode
```