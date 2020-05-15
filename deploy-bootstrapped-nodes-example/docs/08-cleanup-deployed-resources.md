

## Cleaning up resources

### Delete the kubernetes cluster
```
az aks delete --name montest-cluster --resource-group corda-montest-aks
```

### Delete the ACR
```
az acr delete --name corda-montest-acr
```

---
---
