
# The Corda Deployment Initiative 

## Description: 
This repo is all about doing a personal experiment for kubernete based deployment using Corda-based services as a focal point. 

## Objectives: 
- Establish an AKS cluster... keep it running.  Start with a 2 node cluster and adapt as the deployed workloads increase demand. 
- Package and deploy the [Corda sample apps](https://github.com/corda/samples) and deploy them in the AKS cluster adjusting the deployment strategy for each application as necessary, and re-configuring the cluster based on the workload requirement 
- Deploy a 'test-service'... a simple workload to apply new configurations on before expending the effort to apply to nodes.
- capture the learnings in a Gitbook service with video demos of 10min or less embedded in each page.

---
</br> 

## Anticipated learning Experience:

- Understand pod design and workload resource planning for Corda workloads 
- Multi-tenant considerations for Corda workload management (data isolation, auth, resource quota management)
- Ingress routing structure for managing workloads in a multi-tenant cluster
- Explore the usage strategies for the official Corda container 
- Explore devops pipeline design with in-cluster or out-of-cluster devops tooling  
- workload deployment strategies suitable for highly stateful services like Corda workloads
- deployment for the complete set of services including nodes, firewall, and CENM


## Corda Workloads

- auction-cordapp
- autopayroll-CordaService
- bikemarket-TokenSDK
- blacklist
- carinsurance-QueryableState
- constants.properties
- corda-nodeinfo
- cordapp-example
- dollartohousetoken-TokenSDK
- explicit-cordapp-upgrades
- flow-db
- flow-http
- fungiblehousetoken-TokenSDK
- heartbeat
- implicit-cordapp-upgrades
- iou-reactfrontend-Braid
- negotiation-cordapp
- obligation-cordapp
- observable-states
- oracle-example
- ping-pong
- reference-states
- sendfile-Attachments
- spring-webserver
- stockpaydividend-TokenSDK
- timesheet-example
- whistleblower
- yo-cordapp


## Other workloads
- CI Server - Jenkins
- test workload - TBD... an Nginx deploment can be simple or complex a provide interesting learning opportunities 
- Springboot servers - adds value as a front end for Corda nodes
- Hawtio - provides access to metrics, alleviates the user from needing to deploy Hawtio locally
- off-cluster data sources - provide nodes access to off-cluster db's to understand cross-cloud latency issues


Stretch Goals
- Helm - understand designing and deployign workloads as helm charts