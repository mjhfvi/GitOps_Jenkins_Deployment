# <font color="orange">Jenkins IaC Deployment using Helmfile</font>

This README provides instructions on how to deploy Jenkins using Helmfile.
Source Helm Chart: `https://artifacthub.io/packages/helm/jenkinsci/jenkins`

## <font color="purple">Prerequisites</font>

Before you begin, ensure you have the following installed:

- [Helm](https://helm.sh/docs/intro/install/)
- [Helmfile](https://github.com/helmfile/helmfile#installation)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## <font color="purple">Setup</font>

1. Clone the repository containing the Helmfile:

   ```sh
   git clone https://github.com/mjhfvi/GitOpsAutomation.git
   cd GitOpsAutomation/jenkins
   ```

2. Export the required environment variables:

   ```sh
   export HELM_SECRETS_DRIVER=vault
   ```

## <font color="purple">Commands</font>

### Download Dependencies

To download the dependencies specified in the Helmfile, run:

```sh
helmfile deps
```

### Template the Helm Charts

To generate the Kubernetes manifests from the Helm charts, run:

```sh
helmfile template
```

### Deploy Jenkins

Deploy the **Helmfile**, run:

```sh
helmfile sync -f helmfile-jenkins.yaml
```

To deploy Jenkins using **Helm**, run:

```sh
helm install --values=./custom-values.yml jenkins jenkins/jenkins
```

### Apply Changes

To apply only the changes (diff) to the cluster, run:

```sh
helmfile apply
```

### Destroy the Deployment

To destroy the Jenkins deployment, run:

```sh
helmfile destroy
```

## <font color="purple">Post-Deployment Steps</font>

<details><summary></a></summary>
1. Apply the Jenkins service ingress:

```sh
kubectl apply -f jenkins-service-ingress.yaml
```

2. Retrieve the Jenkins admin password:

```sh
kubectl get secret --namespace jenkins jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode
```

3. Port-forward to access Jenkins:

```sh
kubectl port-forward $(kubectl get pods --selector "app.kubernetes.io/instance=jenkins" --output=name) 8080:8080
```

   </details>
