

---
### Run a temporary pod to test building a node (it exits when you leave)
```
kubectl run -it node-test --image=azul/zulu-openjdk:8u192 --restart=Never
```

### Copy a file into the pod (use a different terminal)
```
echo "When 'I' replaced with 'We', even the illness becomes wellness." > file.fil
kubectl cp file.fil node-test:/file.fil
```

### Copy a test node directory into the pod (use a different terminal)
```
kubectl cp andrea node-test:/opt/corda
```

### Expose the ssh port (for crash shell access)
Think from the perspective of the service.
- nodePort: The port on the node where external traffic will come in on
- port: The port of this service
- targetPort The target port on the pods(s) to forward traffic to
- loadbalancer for external access
- Traffic comes in on nodePort, forwards to port on the service which then routes to targetPort on the pods(s).
```
kubectl expose pod node-test --type=LoadBalancer --target-port=2000 --port=2000
```

### Get the loadbalancer's public ip to ssh into the node 
```
ssh testuser@52.141.175.12 -p 2000
>>> run nodeIdentity
```

### Exit the node shell and stop the node
```
>>> run gracefulShutdown
```
### Delete the container
```
$exit
kubectl delete pods node-test
```

## Congratulations! - you've deployed a node manually into a kubernetes pod!

---
 Next: [Deploy the nodes to the cluster](/deploy-bootstrapped-nodes-example/docs/04-deploy-nodes-to-cluster.md)