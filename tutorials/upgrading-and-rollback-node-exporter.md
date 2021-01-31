---
title: How to Upgrade and Rollback node-exporter chart 
description: This tutorial explains how to Upgrade and Rollback node-exporter helm chart
---


### Upgrading node-exporter

It is also important to keep node-exporter helm chart updated. 

To Upgrade node-exporter helm chart,please execute following steps:

**Step 1:** To list all of your current releases in namespace "node-exporter", run the following command :

```execute
helm list -n monitoring
```
You should get output similar to this:

Output:
```
  
```


You need to follow below steps.

**Step 2:** Update your Helm repositories with following command :

```execute
helm repo update 

You can expect the following output:
```
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈ Happy Helming!⎈ 


**Step 3:** Check if there’s a newer version of the node-exporter chart available using following command:

```execute
helm search repo node-exporter --versions
```

You should see output similar to this:

```
NAME                 	CHART VERSION	APP VERSION	DESCRIPTION                                       
bitnami/node-exporter	2.2.0        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	2.1.3        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	2.1.2        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	2.1.1        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	2.1.0        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	2.0.0        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.6        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.5        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.4        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.3        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.2        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.1        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.1.0        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.0.3        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.0.2        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.0.1        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	1.0.0        	1.0.1      	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.14       	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.13       	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.12       	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.11       	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.10       	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.9        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.8        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.7        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.6        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.4        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.3        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.2        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.1        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.2.0        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.1.4        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.1.3        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.1.2        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.1.1        	0.18.1     	Prometheus exporter for hardware and OS metrics...
bitnami/node-exporter	0.1.0        	0.18.1     	Prometheus exporter for hardware and OS metrics...

```

As you can see from the output, there’s a new chart available (version 12.5.0) with node-exporter 2.7.0 (app version). 

**Step 4:** To upgrade your node-exporter release to the latest node-exporter chart, execute below command:

```execute
helm upgrade node-exporter bitnami/node-exporter --namespace  monitoring
```

This command will produce output very similar to the output produced by helm install:

```output

```

**Step 5:** Check updated information about your release using helm list command.

```execute
helm list -n monitoring
```

Output:
```

```

You have successfully upgraded your node-exporter to the latest version of the node-exporter chart.


### Rolling Back a Release

Each time you upgrade a release, a new revision of that release is created by Helm. A revision sets a fixed checkpoint to where you can come back if things don’t work as expected. 
If something goes wrong during the upgrade process, you can always rollback to a previous revision of a given Helm release with the helm rollback command.


If we want to undo the upgrade and rollback our node-exporter release to its previous version, execute following command:

Execute rollback command :

```execute
helm rollback node-exporter 1 -n monitoring
```

Output:

```output
Rollback was a success! Happy Helming!
```

This would rollback the node-exporter installation to its previous release. 



## Upgrading

```bash
$ helm upgrade node-exporter bitnami/node-exporter -n monitoring
```

### To 2.1.0

This version introduces `bitnami/common`, a [library chart](https://helm.sh/docs/topics/library_charts/#helm) as a dependency. More documentation about this new utility could be found [here](https://github.com/bitnami/charts/tree/master/bitnami/common#bitnami-common-library-chart). Please, make sure that you have updated the chart dependencies before executing any upgrade.

### To 2.0.0

[On November 13, 2020, Helm v2 support was formally finished](https://github.com/helm/charts#status-of-the-project), this major version is the result of the required changes applied to the Helm Chart to be able to incorporate the different features added in Helm v3 and to be consistent with the Helm project itself regarding the Helm v2 EOL.

#### What changes were introduced in this major version?

- Previous versions of this Helm Chart use `apiVersion: v1` (installable by both Helm 2 and 3), this Helm Chart was updated to `apiVersion: v2` (installable by Helm 3 only). [Here](https://helm.sh/docs/topics/charts/#the-apiversion-field) you can find more information about the `apiVersion` field.
- The different fields present in the *Chart.yaml* file has been ordered alphabetically in a homogeneous way for all the Bitnami Helm Charts

#### Considerations when upgrading to this version

- If you want to upgrade to this version from a previous one installed with Helm v3, you shouldn't face any issues
- If you want to upgrade to this version using Helm v2, this scenario is not supported as this version doesn't support Helm v2 anymore
- If you installed the previous version with Helm v2 and wants to upgrade to this version with Helm v3, please refer to the [official Helm documentation](https://helm.sh/docs/topics/v2_v3_migration/#migration-use-cases) about migrating from Helm v2 to v3

