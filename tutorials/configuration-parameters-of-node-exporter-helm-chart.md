---
title: Configuration Parameters of node-exporter Helm Chart
description: This tutorial explains about Configuration Parameters
---


### Configuration Parameters of node-exporter Helm Chart

The node-exporter Helm Chart can be customized by specifying configurable Parameters while installing the chart.

The detailed description of these lists of configurable parameters for node-exporter Helm chart with their default values per section/component can be checked at "Parameters" Section of following link:

https://github.com/bitnami/charts/tree/master/bitnami/node-exporter


Specify each parameter using the --set key=value[,key=value] argument to helm install. For example the following command sets the minReadySeconds of the Node Exporter Pods to 120 seconds.

$ helm install my-release --set minReadySeconds=120 bitnami/node-exporter

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

$ helm install my-release -f values.yaml bitnami/node-exporter

**Tip:**  You can use the default values.yaml

**For Configuration Parameters of node-exporter Helm Chartprometheus**


Specify each parameter using the --set key=value[,key=value] argument to helm install. 

For example,

$ helm install --name my-release \
  --set serviceAccount.name=node-exporter  \
    stable/prometheus-node-exporter
    
Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

For example,

$ helm install --name my-release -f values.yaml stable/prometheus-node-exporter
