

This repo is all about doing a personal experiment for a large corda-based deployment on a kubernetes cluster

The rules are simple...
- Establish a single cluster... keep it running successfully as long as possible
- Start with a 2 small cluster nodes which drives understanding for
  - cluster upgrade use case
  - infrastructure monitoring and capacity planning use case (when have my workloads maxed out my deployment)

- package all of the sample cordapps and deploy them in the cluster... drives understanding of:
  - application packaging
  - application resource planning
  - multi-tenant application isolation (early thinking)
  - application resource quota management
  - ingress routing structure
  - understanding and usage of official corda container
  - devops pipeline structure

- its a good exercise for accessing application requirements and delivering a prototype deployment quickly

## Target applications: https://github.com/corda/samples
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


