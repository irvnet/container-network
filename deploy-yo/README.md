# Deploy the Yo corDapp on a Kubernetes cluster
---

Objective: package the Yo cordapp and deploy it to the cluster



---
Planning the Deployment:
- storage: 1gb storage... particularly for h2 vault, config file, credentails, node-info files
- port access: 
  - port access for crash shell
  - port access for p2p access
- cpu requirements:
- memory requirements:
- number of nodes:
- replicas: 1



---

### Create a work area 
mkdir ${HOME}/deploy-yo/work

### Pull the samples repo
```
{
 cd ${HOME}/deploy-yo/work
 git clone git@github.com:corda/samples.git
}
```

### Build the cordapp-yo sample application
```
{
 cd ${HOME}/deploy-yo/work/samples/yo-cordapp 
 ./gradlew jar 
}
```

### create a workspace and add node.conf's for bootstrapping 
```
{
 mkdir -p ${HOME}/deploy-yo/work/build
 cp ${HOME}/deploy-yo/configs/*.conf ${HOME}/deploy-yo/work/build/ 
}

```

### Download the CE Bootstrapper  
```

todo: switch from OS to CE

{
 ${HOME}/deploy-yo/work/build
 curl -O https://software.r3.com/artifactory/corda-releases/net/corda/corda-tools-network-bootstrapper/4.4/corda-tools-network-bootstrapper-4.4.jar
 mv corda-tools-network-bootstrapper-4.4.jar bootstrapper.jar
 java -jar bootstrapper.jar -V
}
```


### Run the bootstrapper and generate the network
`java -jar bootstrapper.jar --dir  ${HOME}/deploy-yo/work/build`


### Add in the dockerfiles for Andrea, Barbara and Notary
```
{
 mkdir -p ${HOME}/deploy-yo/work/build
 cp ${HOME}/deploy-yo/docker/dockerfile.* ${HOME}/deploy-yo/work/build/ 
}
```

### Build & upload andrea image to dockerhub
```
{
 docker build -t andrea-yo -f dockerfile.andrea .
 docker tag andrea-yo irvnet/andrea-yo
 docker push
}
```

### Build & deploy barbara image to dockerhub
```
{
  docker build -t barbara-yo -f dockerfile.barbara .
  docker tag barbara-yo irvnet/barbara-yo
  docker push
}
```


### Build & deploy notary image to dockerhub
```
{
 docker build -t notary-yo -f dockerfile.notary .
 docker tag notary-yo irvnet/notary-yo
 docker push
}
```

### Check current k8s context
```
{
 kubectl config get-contexts
 kubectl config current-context
}
```


### Create manifest files for each node
```
{
 for nodename in notary andrea barbara; do
     kubectl run ${nodename}-yo --image=irvnet/${nodename}-yo --restart=Never --dry-run=client -o yaml > ${nodename}.yml
 done
}
```

### Deploy pods to cluster
```
{
 kubectl create -f andrea-pod.yml
 kubectl create -f barbara-pod.yml
 kubectl create -f notary-pod.yml
 watch kubectl get pods
}

Stop the watch with ctrl-C to return to the command line.

### Expose ports for p2p and crash shell
{
  kubectl expose pod andrea-node --type=LoadBalancer service
}



TODO:
- expose the ssh and p2p port for each node
- pre-req: need to install externaldns so p2p can have FQDN for public access (can use private dns?)
- SEND A YO TRANSACTION from andrea to barbara




