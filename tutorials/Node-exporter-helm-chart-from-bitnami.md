---
title: Sample Tutorial
description: This is a sample tutorial to guide user on creating his own tutorial in md.User should follow exact syntax given below to render in user guide
---

### **1-What is Node Exporter?**

To start using any Bitnami Helm chart, it is necessary to add the Bitnami Helm charts repository to Helm and run the helm install command to deploy this chart.

**BITNAMI NODE EXPORTER CONTAINER HELM CHARTS**

Deploying Bitnami applications as Helm Charts is the easiest way to get started with our applications on Kubernetes. Our application containers are designed to work well together, are extensively documented, and like our other application formats, our containers are continuously updated when new versions are made available.

 Try, test and work with the application in your local environment
 Deploy production-ready applications in your Kubernetes cluster
Install The Node Exporter Chart

To start using any Bitnami Helm chart, it is necessary to add the Bitnami Helm charts repository to Helm and run the helm install command to deploy this chart. Follow these steps:

Add the Bitnami repository to Helm with the following command:

**helm repo add bitnami https://charts.bitnami.com/bitnami
**
A Helm chart describes a specific version of a solution, also known as a “release”. The “release” includes files with Kubernetes-needed resources and files that describe the installation, configuration, usage and license of a chart.

Check that your Kubernetes cluster is running by executing the following command:

**kubectl cluster-info**

Install Node Exporter by running the following:

**NOTE: **Remember that MY-RELEASE is a placeholder, replace it with the name you want to give to the chart or add the --generate-name to give the chart a random name.

**helm install MY-RELEASE bitnami/node-exporter**

**TL;DR**

**helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/node-exporter**

**Introduction**

This chart bootstraps Node Exporter on Kubernetes using the Helm package manager.
Bitnami charts can be used with Kubeapps for deployment and management of Helm Charts in clusters.

###**Prerequisites**

* Kubernetes 1.12+
* Helm 3.0-beta3+

### **2-Why use Bitnami Helm Charts?**

Deploying Bitnami applications as Helm Charts is the easiest way to get started with our applications on Kubernetes. Bitnami ensures that the Helm Charts are always secure, up-to-date, and packaged using industry best practices. Bitnami is able to do this due to the monitoring and packaging automation that we have built throughout the years. When any vulnerability or updates arise for the application, we publish new container images and updated version tags for you to use.

Dynamically replacing values
To start using any Bitnami Helm chart, it is necessary to add the Bitnami Helm charts repository to Helm and run the helm install command to deploy this chart
User can define values as below which needs to be replaced dynamically during run time.

URL :  http://##DNS.IP##:30455


###**Installing the Chart**

Add the bitnami charts repo to Helm:

**helm repo add bitnami https://charts.bitnami.com/bitnami**

To install the chart with the release name my-release:

**helm install my-release bitnami/node-exporter**

The command deploys Node Exporter on the Kubernetes cluster in the default configuration. The configuration section lists the parameters that can be configured during installation.

**Uninstalling the Chart**

**To uninstall/delete the my-release release:**

**helm delete my-release**

The command removes all the Kubernetes components associated with the chart and deletes the release.


###**3-Parameters**

Specify each parameter using the --set key=value[,key=value] argument to helm install. For example the following command sets the minReadySeconds of the Node Exporter Pods to 120 seconds.

**helm install my-release --set minReadySeconds=120 bitnami/node-exporter**

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

**helm install my-release -f values.yaml bitnami/node-exporter**

**Tip:** You can use the default values.yaml

###**Configuration and installation details:**

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.
Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

**Setting Pod's affinity**

This chart allows you to set your custom affinity using the XXX.affinity parameter(s). Find more information about Pod's affinity in the kubernetes documentation.

As an alternative, you can use of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the bitnami/common chart. To do so, set the podAffinityPreset, XpodAntiAffinityPreset, or nodeAffinityPreset parameters.

**Install The Node Exporter Chart**

**NOTE:** To install a Helm chart repository it is necessary to have Helm previously installed and configured in your cluster.

To start using any Bitnami Helm chart, it is necessary to add the Bitnami Helm charts repository to Helm and run the helm install command to deploy this chart. Follow these steps:

Add the Bitnami repository to Helm with the following command:

helm repo add bitnami https://charts.bitnami.com/bitnami

A Helm chart describes a specific version of a solution, also known as a “release”. The “release” includes files with Kubernetes-needed resources and files that describe the installation, configuration, usage and license of a chart.

Check that your Kubernetes cluster is running by executing the following command:

kubectl cluster-info

Install Node Exporter by running the following:

**NOTE:** Remember that MY-RELEASE is a placeholder, replace it with the name you want to give to the chart or add the --generate-name to give the chart a random name.

**helm install MY-RELEASE bitnami/node-exporter**

**Understand Rolling Versus Immutable Tags**

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist. Learn more about Bitnami’s policy on open CVEs.


###**4-Troubleshooting:**

**Upgrading:**

**helm upgrade my-release bitnami/node-exporter**


**To 2.1.0**

This version introduces bitnami/common, a library chart as a dependency. More documentation about this new utility could be found here. Please, make sure that you have updated the chart dependencies before executing any upgrade.

**To 2.0.0**

On Nov 13,2020, Helm v2 support was formally finished, this major version is the result of the required changes applied to the Helm Chart to be able to incorporate the different features added in Helm v3 and to be consistent with the Helm project itself regarding the Helm v2 EOL.


###**What changes were introduced in this major version?**

* Previous versions of this Helm Chart use apiVersion: v1 (installable by both Helm 2 and 3), this Helm Chart was updated to apiVersion: v2 (installable by Helm 3 only). Here you can find more information about the apiVersion field.
* The different fields present in the Chart.yaml file has been ordered alphabetically in a homogeneous way for all the Bitnami Helm Charts

**Considerations when upgrading to this version**

* If you want to upgrade to this version from a previous one installed with Helm v3, you shouldn't face any issues
* If you want to upgrade to this version using Helm v2, this scenario is not supported as this version doesn't support Helm v2 anymore
* If you installed the previous version with Helm v2 and wants to upgrade to this version with Helm v3, please refer to the official Helm documentation about migrating from Helm v2 to v3.
