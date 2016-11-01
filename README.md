# Prometheus on Kubernetes

An example setup of Prometheus inside of Kubernetes, monitoring the Kubernetes
infrastructure itself as well as services running in Kubernetes.

## Preparation

The examples require a running Kubernetes cluster as well as a configured
`kubectl` to talk to that cluster. Check the Kubernetes documentation for
examples.

If you don't have access to a Kubernetes cluster, you can use the [bootkube][]
or [minikube][] projects to start a cluster locally. Bootkube allows for a local
multi-node setup and easier monitoring of Kubernetes components.

You should be able to run `kubectl get pods --all-namespaces` and see some
output:

```
$ kubectl get pods --all-namespaces
NAMESPACE     NAME                                      READY     STATUS    RESTARTS   AGE
kube-system   kube-api-checkpoint-172.17.4.101          1/1       Running   0          35m
kube-system   kube-apiserver-lpd8d                      2/2       Running   0          37m
kube-system   kube-controller-manager-325405546-3ygeg   1/1       Running   0          39m
kube-system   kube-controller-manager-325405546-an3m0   1/1       Running   0          39m
kube-system   kube-dns-v20-3531996453-vkxnp             3/3       Running   0          39m
kube-system   kube-proxy-ks0u7                          1/1       Running   0          37m
kube-system   kube-proxy-zss6m                          1/1       Running   0          17m
kube-system   kube-scheduler-928627977-2mw8x            1/1       Running   0          39m
kube-system   kube-scheduler-928627977-3llcb            1/1       Running   0          39m
```

After install the [kubernetes-dashboard][] the UI should be available at
[http://172.17.4.101:32010](http://172.17.4.101:32010/#/workload?namespace=_all):

```bash
kubectl --namespace=kube-system apply -f https://rawgit.com/kubernetes/dashboard/master/src/deploy/kubernetes-dashboard.yaml
```

[bootkube]: https://github.com/kubernetes-incubator/bootkube
[kubernetes-dashboard]: https://github.com/kubernetes/dashboard
[minikube]: https://github.com/kubernetes/minikube