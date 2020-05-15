

## Create and test an AKS cluster
In this segment you'll use Azure to deploy a kubernetes cluster and an container image repository to store the custom images we'll build. We'll deploy our images from the custom image repostory for the this segment. 

### Login to azure
```
az login
```

### Create a resource group to contain all of the artifacts
```
az group create --name corda-montest-aks --location northcentralus
```

### Create an ACR
```
az acr create --name montestAcr --resource-group corda-montest-aks --sku Standard --location northcentralus
```

### Create an AKS cluster and set the proper context
```
az aks create --resource-group corda-montest-aks --name montest-cluster --node-count 2 --enable-addons monitoring --generate-ssh-keys --node-vm-size Standard_D4s_v3

az aks get-credentials --resource-group corda-montest-aks --name montest-cluster
```

### Attach the ACR to the cluster
This will provide the newly built AKS cluster the authorization to pull images from the ACR we've created for this segment.
```
az aks update --name montest-cluster --resource-group corda-montest-aks --attach-acr montestAcr
```

You have created a an Azure resource group to container the Azure artifacts and in it you have provisioned a 2 node kubernetes cluster, and created an Azure Container Repository to store the images we will create. The custom docker images we will create of our test nodes for Andrea, Barbara and the notary will be pulled from the container repository we've just created.

---

## Test the cluster with a sample deployment
- create a pv and pvc
- create an nginx deployment with a sample web page
- create a deployment
- run the webserver
- create a service and check the rsource in yoru browser
- get a shell and change the web page contents
- delete the deployment



---
 Next: [Test a node deployment](/deploy-bootstrapped-nodes-example/docs/03-test-node-deployment.md)
