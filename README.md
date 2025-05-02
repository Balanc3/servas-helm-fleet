# servas-helm-fleet
deploy servas via helm and fleet


## Pre-requisites
- Kubernetes cluster
- Helm cli installed: https://helm.sh/docs/intro/install/
- Ingress controller installed
- Fleet installed on the target cluster



## Pre-req: Install fleet on target cluster

For detailed or modified installation, refer to here:  https://fleet.rancher.io/quickstart

Quick start: 

```shell
helm repo add fleet https://rancher.github.io/fleet-helm-charts/
helm -n cattle-fleet-system install --create-namespace --wait fleet-crd fleet/fleet-crd
helm -n cattle-fleet-system install --create-namespace --wait fleet fleet/fleet
```

Verify installation and pods are running: 

```shell
kubectl get all -n cattle-fleet-system
```


Should get a response like this: 

```
NAME                                    READY   STATUS    RESTARTS   AGE
pod/fleet-agent-78bf8dd54c-kfqcv        1/1     Running   0          39m
pod/fleet-controller-66d5944cf5-9vsz9   3/3     Running   0          39m
pod/gitjob-5b796c7d9-x49qp              1/1     Running   0          39m

NAME                                  TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/gitjob                        ClusterIP   10.43.169.73    <none>        80/TCP     39m
service/monitoring-fleet-controller   ClusterIP   10.43.103.216   <none>        8080/TCP   39m
service/monitoring-gitjob             ClusterIP   10.43.59.112    <none>        8081/TCP   39m

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/fleet-agent        1/1     1            1           39m
deployment.apps/fleet-controller   1/1     1            1           39m
deployment.apps/gitjob             1/1     1            1           39m

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/fleet-agent-78bf8dd54c        1         1         1       39m
replicaset.apps/fleet-controller-66d5944cf5   1         1         1       39m
replicaset.apps/gitjob-5b796c7d9              1         1         1       39m
```

Make sure pods have status of "running" 


If you have more than one cluster that you would like to deploy to, register down stream clusters by folowing directions here: https://fleet.rancher.io/cluster-registration


## Pre-req: If you don't have an ingress controller

Change fleet.yaml so the ingress controller will be managed by helm: 

```powershell
(Get-Content .\charts\ingress-controller\fleet.yml).replace("true","false") | Set-Content .\charts\ingress-controller\fleet.yml
```

## 






