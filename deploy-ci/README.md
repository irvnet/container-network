

---

## Objective: 
- Establish a build and deploy pipeline for cordapp development

## Description: 
In this tutorial  we will establish a pipeline for cordapp build and deployment. Our target for deployment will be an AKS cluster.


To establish our pipeline we will consider 2 different possibilities... [Travis CI](https://docs.travis-ci.com/user/for-beginners/) using build as a service, and [Jenkins](https://www.jenkins.io/) tooling which we'll deploy to our AKS cluster.


Prerequisites
- Jenkins [docker image](https://hub.docker.com/r/jenkins/jenkins)
- Access to an AKS cluster
- Access to a [Travis CI](https://travis-ci.com/signup) account



## Resources (Travis CI)

https://medium.com/bestcloudforme/travis-ci-aks-azure-kubernetes-service-zero-downtime-continuous-deployment-case-study-eng-ee5d1de256f2

https://docs.travis-ci.com/user/deployment/releases/

https://cloud.google.com/solutions/continuous-delivery-with-travis-ci

https://kumorilabs.com/blog/k8s-8-continuous-deployment-travis-ci-kubernetes/

https://gist.github.com/nickbclifford/16c5be884c8a15dca02dca09f65f97bd

https://medium.com/angular-in-depth/the-angular-devops-series-ct-ci-with-travis-ci-and-github-pages-3c02664f078



---


## Resources (Jenkins deployment)


### good overview of an aks based jenkins deployment
https://www.youtube.com/watch?v=eRWIJGF3Y2g
- use an azure file-share (keep the files outside the cluster for flexibility)
- https://github.com/marcel-dempers/docker-development-youtube-series/tree/master/jenkins

https://github.com/GoogleCloudPlatform/continuous-deployment-on-kubernetes/blob/master/sample-app/Jenkinsfile

https://plugins.jenkins.io/kubernetes-cd/

https://www.magalix.com/blog/create-a-ci/cd-pipeline-with-kubernetes-and-jenkins

https://kubernetes.io/blog/2018/04/30/zero-downtime-deployment-kubernetes-jenkins/

https://cloud.google.com/solutions/continuous-delivery-jenkins-kubernetes-engine

https://rancher.com/blog/2018/2018-11-27-scaling-jenkins/

https://medium.com/containerum/configuring-ci-cd-on-kubernetes-with-jenkins-89eab7234270

https://medium.com/velotio-perspectives/continuous-deployment-with-azure-kubernetes-service-azure-container-registry-jenkins-ca337940151b

https://docs.microsoft.com/en-us/azure/developer/jenkins/deploy-from-github-to-aks

https://docs.microsoft.com/en-us/azure/developer/jenkins/deploy-to-aks-using-blue-green-deployment-pattern

---

## Applying deployment Strategies to Corda 

### What deployment strategies optimize Corda deployments (considering they're highly stateful)? 
- Blue-green deployment: 
  - possibly: if cutover means you stop the old node just before starting the new one. Other strategies may not apply considering Corda can only ever have one instance of a legal name running on a network. 
  - use case: upgrade - corda deployments can be lengthy. To minimize downtime can take this strategy with a keen focus on the timing of turning old service down immediately before turning up the new one.
  - https://docs.microsoft.com/en-us/azure/developer/jenkins/deploy-to-aks-using-blue-green-deployment-pattern


- Canary Deployment:
  - possibly: may be relevant when upgrading all the available nodes to a new corda version in the cluster. Assuming the workloads will all be custom built images based on the official corda image, upgrading the customer image to be based on a new version of the corda container, or the workload deployment to a new configuration,  may apply for this strategy

### Resources (Deployment Strategy)
- https://dev.to/mostlyjason/intro-to-deployment-strategies-blue-green-canary-and-more-3a3
- https://techbeacon.com/devops/bulletproof-devops-strategy-ensure-success-cloud
- https://docs.openshift.com/container-platform/3.7/dev_guide/deployments/deployment_strategies.html
- https://medium.com/velotio-perspectives/exploring-upgrade-strategies-for-stateful-sets-in-kubernetes-c02b8286f251
- https://dzone.com/articles/docker-and-devops-developing-state-full-applicatio



