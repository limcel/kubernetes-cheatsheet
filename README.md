# kubernetes-cheatsheet

```
-- get all pods
 kubectl get pods --all-namespaces

-- get pods with namespace
kubectl get pods --namespace={namespace}

kubectl get svc
kubectl get ingress

-- view pod logs
kubectl logs linkanalysis-deployment-ff5c87bf-8qrz2 --namespace {namespace}
kubectl logs linkanalysis-deployment-ff5c87bf-98rk5 --namespace {namespace}
kubectl logs aws-load-balancer-controller-64ccc6b4df-ht4cg --namespace kube-system

-- view deployments
kubectl get deployment --namespace={namespace}

-- delete unwanted services
kubectl delete -f rds.yaml

-- delete everything in a certain namespace
kubectl delete all --all -n {namespace}

-- get kubernetes secrets
kubectl get secrets

-- to retrieve secret variable
kubectl get secret <your_secret_name> -o jsonpath='{.data}'
-- decode variable
echo '<your_string_here>' | base64 --decode
```