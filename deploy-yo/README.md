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

### Download the bootstrapper  
```
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

 ### build & upload andrea image to dockerhub
 ```
{
 docker build -t andrea-yo -f dockerfile.andrea .
 docker tag andrea-yo irvnet/andrea-yo
 docker push
}
```

 ### build & deploy barbara image to dockerhub
 ```
{
 docker build -t barbara-yo -f dockerfile.barbara .
 docker tag barbara-yo irvnet/barbara-yo
 docker push
}
```


 ### build & deploy notary image to dockerhub
```
{
 docker build -t notary-yo -f dockerfile.notary .
 docker tag notary-yo irvnet/notary-yo
 docker push
}
```

TODO:
- ADD WEB SERVER
- CREATE K8S RESOURCE FILES WITH DRY-RUN
- DEPLOY NODE AND WEBSERVER
- SEND A YO TRANSACTION










