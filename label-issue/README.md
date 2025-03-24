## Missing Label Selector in Service Object

In this demo, we intentionally create a Deployment and Service with a `missing label selector` issue to verify if K8SGPT can detect it and provide a solution.

Use the following command to create the Deployment and Service with the `missing label selector` issue in your cluster:
```bash
kubectl apply -f missing-label-deploy-service.yaml
```

### Analyze the Issue Using K8SGPT

Run the commands below to analyze the issue:
```bash
k8sgpt analyze
k8sgpt analyze --explain --backend google
```
