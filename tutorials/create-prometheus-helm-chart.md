# kube-prometheus

[kube-prometheus](https://github.com/prometheus-operator/kube-prometheus) collects Kubernetes manifests to provide easy to operate end-to-end Kubernetes cluster monitoring with Prometheus using the Prometheus Operator.

## TL;DR

```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ kubectl create ns monitoring
$ helm install prometheus bitnami/kube-prometheus -n monitoring
```

## Introduction

This chart bootstraps [Prometheus Operator](https://github.com/bitnami/bitnami-docker-prometheus-operator) on [Kubernetes](http://kubernetes.io) using the [Helm](https://helm.sh) package manager.

In the default configuration the chart deploys the following components on the Kubernetes cluster:

- [Prometheus Operator](https://github.com/prometheus-operator/prometheus-operator)
- [Prometheus](https://github.com/prometheus/prometheus/)
- [Alertmanager](https://github.com/prometheus/alertmanager)

**IMPORTANT**

Only one instance of the Prometheus Operator component should be running in the cluster. If you wish to deploy this chart to **manage multiple instances** of Prometheus in your Kubernetes cluster, you **have to disable** the installation of the Prometheus Operator component using the `operator.enabled=false` chart installation argument.

Bitnami charts can be used with [Kubeapps](https://kubeapps.com/) for deployment and management of Helm Charts in clusters.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.1.0

## Installing the Chart

Add the `bitnami` charts repo to Helm:

```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
```

To install the chart with the release name `prometheus`:

```bash
$ helm install prometheus bitnami/kube-prometheus -n monitoring
```

Install grafana

```bash
helm install grafana bitnami/grafana --set service.type=NodePort --set admin.password=GRAFANA_PASSWORD -n monitoring

The command deploys kube-prometheus on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list -n monitoring`