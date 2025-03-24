## Deployment with Insufficient CPU Resources

In this demo, we intentionally create a deployment with insufficient CPU resource limits to verify if K8SGPT can detect the issue and provide a solution.

### Steps to Reproduce

Run the following command to create a deployment with insufficient CPU resource limits in your cluster:
```bash
kubectl apply -f insufficient-cpu-deploy.yaml
```

### Analyze the Issue Using K8SGPT

Use the commands below to analyze the issue:
```bash
k8sgpt analyze
k8sgpt analyze --explain --backend google
```
