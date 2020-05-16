
# Deploy a SpringBoot Webserver

### Objective: In this exercise you will deploy a springboot webserver. To save time, the springboot webserver has already been created for you. The source code is available [here](#) if you'd like to make updates and deploy them into the environment... however, this execrise is more focused on packaging and usage of the service more than creating the service.


TODO:
- add environment variables for reused resource names (cluster, acr)


---


## Create a web interface for the nodes

### create a test springboot web server
In this section we will test a simple springboot webserver and instrument it with the Jolokia driver. This will come in handy when we create a webserver to enable the node with a webserver which will accept incoming http requests and tickle the corresponding  flow as an integration mechanism


- create a simple springboot web server and test
- containerize the springboot web server and deploy
- expose the web port for the webserver and test
- add a custom route and redeploy/test the http route
- add jolokia driver and redeploy/test the jolokia endoint
- configure git/jenkins to do the deployment


## Add the springboot web server to the pod
In this section we'll containerize the springboot webserver and add it to the pod with the node
notes:
- provide a description of the sidecar pattern



- create and test a simple springboot web server and test
- modify the web server to add routes that coincide with the flows
- configure the uncontainerized andrea-node to recognize the webserver and test

### containerize the sprintboot webserver


 Next: [Cleanup deploy resources](/deploy-bootstrapped-nodes-example/docs/08-cleanup-deployed-resources.md)

