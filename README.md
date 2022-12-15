# flux-remote-cluster

This an example repository that uses a single Flux instance to deploy workloads on remote clusters.

Flux is bootstraped on both the management Cluster and remote Clusters. Workloads will be deployed on the remote Clusters via the Flux instance running on the management Cluster. To do so, we provide the kubeconfig Secret of the matching remote Cluster and Flux will use it for deploying workloads.

Create the kubeconfig for the remote clusters on the management cluster running flux:
```sh
kubectl create secret generic -n flux-system kubeconfig-staging --from-file=value.yaml=<STAGING-KUBECONFIG-PATH>
kubectl create secret generic -n flux-system kubeconfig-production --from-file=value.yaml=<PRODUCTION-KUBECONFIG-PATH>
```
