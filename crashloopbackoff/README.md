## Pod CrashLoopBackOff Due to ImagePullBackOff

In this demo, we intentionally create a `Pod CrashLoopBackOff` issue caused by `ImagePullBackOff` to verify if K8SGPT can detect it and provide a solution.

Use the following command to create a pod in the cluster with the `CrashLoopBackOff/ImagePullBackOff` issue:
```
kubectl apply -f crashloopbackoff-pod.yaml
```

#### Analyze the Issue Using K8SGPT

Run the following commands to analyze the issue:
```
k8sgpt analyze
k8sgpt analyze --explain --backend google
```
