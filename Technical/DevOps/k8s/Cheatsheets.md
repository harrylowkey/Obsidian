## Clusters
```
### **Get cluster info:**

- k cluster-info

```bash
kubectl api-resources —namespaced=false //global namespaces
kubectl api-resources —namespaced=true //bound to namespace
````

## Get all resources

```bash
k get all
```

## Formatting Output

```
kubectl [command] [TYPE] [NAME] -o <output_format>

Here are some of the commonly used formats:

1. `-o json` Output a JSON formatted API object.
2. `-o name` Print only the resource name and nothing else.
3. `-o wide` Output in the plain-text format with any additional information.
4. `-o yaml` Output a YAML formatted API object.
$ kubectl create namespace test-123 --dry-run -o yaml
```

### **Scale instances :**

- of `deployment`

```bash
k scale --replicas=n <resource-type> <resource-name>

# with namespace
kubectl -n <namespace> scale deployment/esg-materiality-backend-dev-backend --replicas=3

# of file
k scale --replicas=3 -f <file-name>

# relicaset resource
k scale --replicas=3 replicaset myapp-replicaset

# update replicas in file and replace file change
k replace -f <file-name>
```

### CRUD  resource:

1. CU with file
```bash
# with file
k create -f <file-name>
k apply -f <file-name>
```

## Services

1. Get services

```bash
kubectl get services -A // -A: list all services
```

## Pods

1. Get pods

```bash
kubectl get pods -A // get all pods in a
kubectl get pods -o wide // get pod with IP
```

2. Delete pods that is not running:

```
kubectl delete pods --field-selector=status.phase!=Running
```

3. Create pods
```
# with file
k create -f <file-name>

# imperative 
k run *pod-name* --image=*image-name*

# create pod with review and output to file
k run my-pod --image=nginx --dry-run=client -o yam > pod-definition.yaml

# imperative command to update image
kubectl set image <object_type>/<object_name> <container_name>=<new_image>

# if you are not given a pod definition file, you may extract the definition to a file using the below command:
$ kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```

4. Edit pods:
```
k edit pod/<pod-name>
k replace --force -f <temp-file-name>
```

6. Check which node that pod is located
```
k get pods -o wide
```

5. Access **into pod:**
```
k -n <namespace> exec -it <pod-name> -- /bin/sh
```

6. Forward pod
```
 kubectl -n <namespace> port-forward <pod-name> 5433(host-port):5432(container-pod)
```


## Namespaces

```
k create namespace dev
k create -f namespace-dev.yml
kg ns
```

- Under the same namespace, service can connect to another service using service-name
- To connect to service in another namespace, we need to connect to its DNS

## Deployments

1. CRUD deployment
```bash
kubectl delete deployment <filename>
kubectl get deployments
k create deployment nginx --image=nginx --replicas=4 --dry-run -o yaml
```

## Storages

1. Get storages

```bash
kubectl get storageclass
```

2. Describe **storage info:**

```bash
kubectl describe storageclass
```

## Secrets

1. CRUD secrets

```bash
kubectl create secret generic/tls <name> —from-literal KEY=value
kubectl get secrets
```
