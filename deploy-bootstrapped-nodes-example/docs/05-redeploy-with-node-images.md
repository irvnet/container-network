
---

In this segment we will re-create our nodes using the official Corda containers

## Designing the deployment

Notes:
- outline the resources a node needs for deployment (storage, ports, services, etc)
- provide a diagram of the finished deployment
- introduce initial registration? (maybe later... can use bootstrapped official containers)
- include CENM deployment (maybe)
- use config maps
  - check out chart.txt to see how it was done in corda-kubernetes-internal
   - add as a separate optional tutorial with a link in this document
   - as a 'bonus' segment refer them to the CENM deployment tutorial then demonstrate registering against an idmgr
   - as a separate tutorial with a link in this document to register against in a separate namespace (or a separate cluster)

---
## Resources

Config maps provide configuration, and if necessary executable scripts

https://kubernetes.io/docs/concepts/configuration/configmap/
https://stackoverflow.com/questions/41674108/how-to-include-script-and-run-it-into-kubernetes-yaml



---
 Next: [Review node metrics](/deploy-bootstrapped-nodes-example/docs/06-review-node-metrics.md)
