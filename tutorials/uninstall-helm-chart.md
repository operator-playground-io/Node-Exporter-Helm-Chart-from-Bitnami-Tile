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

```output

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
