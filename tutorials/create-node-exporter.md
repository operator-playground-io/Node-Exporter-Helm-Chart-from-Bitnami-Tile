# Node Exporter

[Node Exporter](https://github.com/prometheus/node_exporter) is a Prometheus exporter for hardware and OS metrics exposed by *NIX kernels, written in Go with pluggable metric collectors.

## TL;DR

```bash
$ kubectl create ns monitoring
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm install node-exporter bitnami/node-exporter -n monitoring
```

## Introduction

This chart bootstraps [Node Exporter](https://github.com/bitnami/bitnami-docker-node-exporter) on [Kubernetes](http://kubernetes.io) using the [Helm](https://helm.sh) package manager.

Bitnami charts can be used with [Kubeapps](https://kubeapps.com/) for deployment and management of Helm Charts in clusters.

## Prerequisites

- Kubernetes 1.12+
- Helm 3.1.0

## Installing the Chart

Add the `bitnami` charts repo to Helm:

```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
```

To install the chart with the release name `node-exporter`:

```bash
$ helm install node-exporter bitnami/node-exporter -n monitoring
```

The command deploys Node Exporter on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.


Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install node-exporter -f values.yaml bitnami/node-exporter -n monitoring
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Configuration and installation details

### [Rolling VS Immutable tags](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/)

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

### Setting Pod's affinity

This chart allows you to set your custom affinity using the `XXX.affinity` parameter(s). Find more information about Pod's affinity in the [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity).

As an alternative, you can use of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the [bitnami/common](https://github.com/bitnami/charts/tree/master/bitnami/common#affinities) chart. To do so, set the `podAffinityPreset`, `XpodAntiAffinityPreset`, or `nodeAffinityPreset` parameters.

## Troubleshooting

Find more information about how to deal with common errors related to Bitnami’s Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).
