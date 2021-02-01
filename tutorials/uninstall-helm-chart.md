---
title: How to Uninstall node-exporter Helm chart 
description: This tutorial explains how to Uninstall node-exporter helm chart
---

### Uninstall node-exporter Helm Chart

Check your deployed node-exporter helm chart:

```execute
 helm list -n monitoring
```

 Output will be similar:

```
NAME      	NAMESPACE 	REVISION	UPDATED                                	STATUS  	CHART                	APP VERSION
grafana   	monitoring	1       	2021-01-31 14:49:44.452869427 -0600 CST	deployed	grafana-5.1.0        	7.3.7      
prometheus	monitoring	2       	2021-01-31 14:52:20.860742559 -0600 CST	deployed	kube-prometheus-3.6.0	0.45.0   
```

To uninstall the node-exporter helm chart, use the helm delete command:

```execute
helm delete node-exporter -n monitoring
```

Output:

```output
release "node-exporter" uninstalled
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

```execute
helm status node-exporter -n monitoring
```

Output:

```
Error: node-exporter: not found
```
