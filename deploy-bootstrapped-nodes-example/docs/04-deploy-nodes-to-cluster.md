
---

## Create a deployment for each node
Now that we have a better idea of how to create and populate a container, let's make it more persistent and repeatable. 
In this segment we will:
- build a custom image for each node based on the azul image
- upload our custom image to an ACR
- deploy the custom image to the cluster
- create a deployment resource file for each node to make it repeatable

### Create a dockerfile for the andrea node
```
cat > dockerfile.andrea <<EOF
FROM azul/zulu-openjdk:8u192

## Add packages, clean cache, create dirs, create corda user and change ownership
RUN apt-get update && \
    rm -rf /var/lib/apt/lists/* && \
    addgroup corda && \
    useradd corda -g corda -m -d /opt/corda

# copy our bootstrapped andrea node into /opt/corda
COPY --chown=corda:corda andrea/  /opt/corda
COPY --chown=corda:corda scripts/run.sh   /opt/corda/run.sh

USER "corda"

ENV P2P_ADDRESS=10200 \
    RPC_ADDRESS=10201 \
    ADM_ADDRESS=10202 \
    SSH_ADDRESS=2000  \
    PATH=$PATH:/opt/corda/bin

EXPOSE ${P2P_ADDRESS} ${RPC_ADDRESS} ${ADM_ADDRESS} ${SSH_ADDR}
WORKDIR /opt/corda
ENV HOME=/opt/corda

ENTRYPOINT ["/opt/corda/run.sh"]
EOF
```

### Build the docker image
```
docker build -f dockerfile.andrea -t node-andrea .
```

### Check that the image has been built correctly
```
docker images
```

### Run the container locally 
```
docker run -p 2000:2000 -d node-andrea
```

### Check that the container is running correctly
```
docker ps -a
```

### Connect to the running container's node-shell
```
ssh -p 2000 testuser@localhost
```

### Validate the nodes identity
```
>>> run nodeInfo
```



## Congratulations - you've built and deployed your custom image locally

---

### Upload and deploy to the kubernetes cluster
- tag the images
- upload the images to the ACR 

### Create a deployment for node-andrea
```
kubectl create deployment node-andrea --image=nginx --dry-run=client -o yaml > node-andea-deployment.yml
kubectl create -f node-andea-deployment.yml 
kubectl exec -it <POD-NAME> -- /bin/bash
```

### Create a loadbalancer port and ssh into the node-shell
- kubectl expose ***
- kubectl get service to see the lb's public ip 
- ssh into the node-shell

### Create a deployment for node-barbara
```
kubectl create deployment node-barbara --image=nginx --dry-run=client -o yaml > node-barbara-deployment.yml
kubectl create -f node-barbara-deployment.yml 
kubectl exec -it <POD-NAME> -- /bin/bash
```

### Create a deployment for node-notary
```
kubectl create deployment node-notary --image=nginx --dry-run=client -o yaml > node-notary-deployment.yml
kubectl create -f node-notary-deployment.yml 
kubectl exec -it <POD-NAME> -- /bin/bash
```

### Create cluster ip('s) for internal p2p comms?

Congratulations! - you have created deployments for your custom images

---

 Next: [Redeploy with R3 official node images](/deploy-bootstrapped-nodes-example/docs/05-redeploy-with-node-images.md)
