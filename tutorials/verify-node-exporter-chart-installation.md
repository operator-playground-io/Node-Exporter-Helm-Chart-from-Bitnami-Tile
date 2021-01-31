---
title: Verify node-exporter Chart Installation
description: This tutorial explains how to verify that node-exporter chart installed successfully
---


Once the helm chart installation done you need to verify all the pods and services are up and running.

Execute below command to check status of pods and services: 

### Check the pod status


```execute
kubectl get pods --namespace monitoring
```

You will see similar to this output:

```
NAME                                                     READY   STATUS    RESTARTS   AGE
alertmanager-prometheus-kube-prometheus-alertmanager-0   2/2     Running   0          4m40s
grafana-envvars-fdc5499fc-4gt55                          0/1     Pending   0          4m11s
prometheus-kube-prometheus-operator-db9ff65fd-jv8qk      1/1     Running   0          4m51s
prometheus-kube-state-metrics-7b6554ccf-57fx6            1/1     Running   0          4m51s
prometheus-node-exporter-7xmd7                           1/1     Running   0          4m51s
prometheus-prometheus-kube-prometheus-prometheus-0       2/2     Running   1          4m40s

```

It may take few minutes to change the `STATUS` from `ContainerCreating` to `Running`. 


Once the `node-exporter` PODs are up and running , and `READY` states are `1/1`, your node-exporter is ready to use.

### Check all the Kubernetes resources status

You can run the following command to know status of all the deployed resources inside the namespace `node-exporter`


```execute
kubectl get all --namespace monitoring
```

All the deployment and service status should be Running.

```
NAME                                                     READY   STATUS    RESTARTS   AGE
alertmanager-prometheus-kube-prometheus-alertmanager-0   2/2     Running   0          4m40s
grafana-envvars-fdc5499fc-4gt55                          0/1     Pending   0          4m11s
prometheus-kube-prometheus-operator-db9ff65fd-jv8qk      1/1     Running   0          4m51s
prometheus-kube-state-metrics-7b6554ccf-57fx6            1/1     Running   0          4m51s
prometheus-node-exporter-7xmd7                           1/1     Running   0          4m51s
prometheus-prometheus-kube-prometheus-prometheus-0       2/2     Running   1          4m40s
[student@event-k8s-ibm-operators-playground-cgdaoc ~]$ kubectl get all --namespace monitoring
NAME                                                         READY   STATUS    RESTARTS   AGE
pod/alertmanager-prometheus-kube-prometheus-alertmanager-0   2/2     Running   0          5m26s
pod/grafana-envvars-fdc5499fc-4gt55                          0/1     Pending   0          4m57s
pod/prometheus-kube-prometheus-operator-db9ff65fd-jv8qk      1/1     Running   0          5m37s
pod/prometheus-kube-state-metrics-7b6554ccf-57fx6            1/1     Running   0          5m37s
pod/prometheus-node-exporter-7xmd7                           1/1     Running   0          5m37s
pod/prometheus-prometheus-kube-prometheus-prometheus-0       2/2     Running   1          5m26s

NAME                                              TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/alertmanager-operated                     ClusterIP   None             <none>        9093/TCP,9094/TCP,9094/UDP   5m26s
service/grafana                                   NodePort    10.105.233.226   <none>        3000:32588/TCP               4m57s
service/prometheus-kube-prometheus-alertmanager   ClusterIP   10.108.49.18     <none>        9093/TCP                     5m37s
service/prometheus-kube-prometheus-operator       ClusterIP   10.110.239.42    <none>        8080/TCP                     5m37s
service/prometheus-kube-prometheus-prometheus     ClusterIP   10.106.147.234   <none>        9090/TCP                     5m37s
service/prometheus-kube-state-metrics             ClusterIP   10.104.20.107    <none>        8080/TCP                     5m37s
service/prometheus-node-exporter                  ClusterIP   10.100.202.189   <none>        9100/TCP                     5m37s
service/prometheus-operated                       ClusterIP   None             <none>        9090/TCP                     5m26s

NAME                                      DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
daemonset.apps/prometheus-node-exporter   1         1         1       1            1           <none>          5m37s

NAME                                                  READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/grafana-envvars                       0/1     1            0           4m57s
deployment.apps/prometheus-kube-prometheus-operator   1/1     1            1           5m37s
deployment.apps/prometheus-kube-state-metrics         1/1     1            1           5m37s

NAME                                                            DESIRED   CURRENT   READY   AGE
replicaset.apps/grafana-envvars-fdc5499fc                       1         1         0       4m57s
replicaset.apps/prometheus-kube-prometheus-operator-db9ff65fd   1         1         1       5m37s
replicaset.apps/prometheus-kube-state-metrics-7b6554ccf         1         1         1       5m37s

NAME                                                                    READY   AGE
statefulset.apps/alertmanager-prometheus-kube-prometheus-alertmanager   1/1     5m26s
statefulset.apps/prometheus-prometheus-kube-prometheus-prometheus       1/1     5m26s

```
