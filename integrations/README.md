# Filters and Integrations

This demo covers the concepts of filters and integrations features provided by K8SGPT.

## Filters
Filters are used to narrow down Kubernetes objects for K8SGPT analysis using LLM.

To list supported filters, use the following command:
```
k8sgpt filters list
```

To filter analysis based on Kubernetes objects, use:
```
k8sgpt analyze --filter Deployment --namespace default --backend google --explain
```

## Integrations
K8SGPT offers integration with other tools. Once an integration is added, its resources can be used as additional filters.

To list supported integrations, use:
```
k8sgpt integrations list
```

Currently supported integrations:
```
- aws
- keda
- kyverno
- prometheus
```

For this demo, we will use the Kyverno integration.

### Kyverno
The Kyverno project provides a comprehensive set of tools to manage the complete Policy-as-Code (PaC) lifecycle for Kubernetes and other cloud-native environments.

Before proceeding with the demo, install Kyverno in your cluster as an operator:
```
helm repo add kyverno https://kyverno.github.io/kyverno/
helm repo update
helm install kyverno kyverno/kyverno -n kyverno --create-namespace
```

## Integrations and Filters Demo
- After installing Kyverno, check the filters to verify additional filters related to Kyverno:
    ```
    k8sgpt filters list
    ```

- Create a set of Kubernetes objects before applying the demo Kyverno policy.

- Apply the cluster policy created for this demo:
    ```
    kubectl apply -f cluster-policy.yaml
    ```
    - This policy enforces that each object created in the Kubernetes cluster must have a label called `team`.

- Apply a sample pod to test the policy:
    ```
    kubectl apply -f pod.yaml
    ```
    - This will throw an error indicating that the pod does not have the required `team` label.

## K8SGPT Analysis
K8SGPT can analyze the cluster and identify objects violating the applied policy. Use the following command to analyze and filter out the violated objects in the Kubernetes cluster:
```
k8sgpt analyze --filter PolicyReport --namespace default --backend google --explain
```
