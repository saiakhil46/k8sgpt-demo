# K8S and K8SGPT Local Setup

#### KIND Cluster Installation 

For macOS, execute the following command to install the KIND binary:
```bash
brew install kind
```

Refer to this [documentation](https://kind.sigs.k8s.io/docs/user/quick-start/#installing-with-a-package-manager) for installation instructions on other operating systems.

#### K8SGPT Binary Installation
For macOS, execute the following commands to install the K8SGPT binary:
```bash
brew tap k8sgpt-ai/k8sgpt
brew install k8sgpt
```

Refer to this [documentation](https://docs.k8sgpt.ai/getting-started/installation) for installation instructions on other operating systems.

#### KIND Local Kubernetes Cluster Creation
The following command creates a single-node Kubernetes cluster:
```bash
kind create cluster --name k8sgpt-demo
```

To create a multi-node Kubernetes cluster, save the following configuration in a file, such as `multi-node-k8s-cluster.yaml`:
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
    - role: control-plane
    - role: worker
    - role: worker
```

Then, use the following command to create the multi-node Kubernetes cluster using the configuration file:
```bash
kind create cluster --name multi-node-k8s-cluster --config multi-node-k8s-cluster.yaml
```

#### K8SGPT Backend Configuration
The backend is the LLM model used to analyze issues in the Kubernetes cluster.

To list supported backends, use the following command:
```bash
k8sgpt auth list
```

Below is the list of backends supported by K8SGPT:
```
> openai
> localai
> ollama
> azureopenai
> cohere
> amazonbedrock
> amazonsagemaker
> noopai
> huggingface
> googlevertexai
> oci
> customrest
> ibmwatsonxai
```

For this demo, we are using Google's Gemini LLM model called `gemini-2.0-flash`.

Use the following command to configure the backend:
```bash
k8sgpt auth add --backend google --model gemini-2.0-flash --password "<YOUR_API_KEY>"
```

> **Note:** Replace `<YOUR_API_KEY>` with your actual API key. Avoid sharing sensitive information in public documentation.
