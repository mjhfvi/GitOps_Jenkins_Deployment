# Commands to deploy:

# helmfile deps # < download dependencies

# helmfile template # < template stuff. You might have to be signed into vault

# helmfile sync # < deploy everything

# helmfile sync -f filename.yaml # < deploy everything from file

# helmfile apply # < deploy diff only

# helmfile destroy # < deploy diff only

## kubectl -f jenkins-service-ingress.yaml apply

## kubectl -f jenkins-persistent-volume-nfs.yaml apply

## kubectl -f jenkins-persistent-volume-claim.yaml apply

# helmfile -f helmfile-jenkins.yaml apply

# What is a helmfile? Read here... https://github.com/helmfile/helmfile

# Examples: https://github.com/helmfile/helmfile/blob/main/examples/charts/argocd-helmfile-deployment/helmfile.yaml

# Before deployment, export the required env vars

# export HELM_SECRETS_DRIVER=vault
