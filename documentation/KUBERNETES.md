### Setup Storage

2. Apply the Jenkins persistent volume and claim:

   ```sh
   kubectl apply -f jenkins-persistent-volume-nfs.yaml
   kubectl apply -f jenkins-persistent-volume-claim.yaml
   ```

## Troubleshooting

4. Patch the Jenkins persistent volume:

   ```sh
   kubectl patch pv jenkins-storage-persistent-volume-nfs -p '{"spec":{"claimRef": null}}'
   ```

## kubectl get secret --namespace jenkins jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode

## kubectl patch pv jenkins-storage-persistent-volume-nfs -p '{"spec":{"claimRef": null}}'

# kubectl port-forward $(kubectl get pods --selector "app.kubernetes.io/instance=jenkins" --output=name) 8080:8080
