# Demo on K8sGPT Operator

#### Installing the K8sGPT Operator
To install the operator, run the following commands:
```bash
helm repo add k8sgpt https://charts.k8sgpt.ai/
helm repo update
helm install release k8sgpt/k8sgpt-operator -n k8sgpt-operator-system --create-namespace
```

#### Deploying a Google API Secret
You need to create a Kubernetes secret for your Google API token. Use the following command:
```bash
kubectl create secret generic k8sgpt-sample-secret --from-literal=google-api-key=$GOOGLE_TOKEN -n k8sgpt-operator-system
```

#### Deploying a K8sGPT Resource
To deploy a K8sGPT resource, apply the following manifest:
```bash
kubectl apply -f k8sgpt-object.yaml
```

#### Viewing Results from the K8sGPT Operator
To view the continuous results collected by the K8sGPT operator, execute the following command:
```bash
kubectl get results -o json -n k8sgpt-operator-system | jq .
```
