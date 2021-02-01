###**What is Prometheus?**

Prometheus is free of cost software that is used to monitor events and Alerting tools. It helps to record live metrics in a timestamp series database using Http model with n number of queries and real-time alerting.


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
```

The command deploys kube-prometheus on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list -n monitoring`


**Prometheus Monitoring** 

Prometheus Monitoring is fast becoming one of the Docker and Kubernetes monitoring tool to use. This guide explains how to implement Kubernetes monitoring with Prometheus. You will learn how to deploy Prometheus server, metrics exporters, setup kube-state-metrics, pull, scrape and collect metrics, configure alerts with Alertmanager and dashboards with Grafana. We’ll cover how to do this manually as well as by leveraging some of the automated deployment/install methods like Prometheus operators.

**Prometheus Monitoring setup** 

We can monitor full Kubernetes cluster end to end with Prometheus.

1-The Prometheus stack includes:
2-Prometheus
3-Alertmanager
4-Kube-state-metrics
5-node-exporter
6-Grafana

We can also include alerts and dashboards in it !!

Capacity planning

Cluster health

Deployments

k8s cluster rsrc use

k8s node rsrc use

k8s resources cluster

k8s resources namespace

k8s resources pod

kube DNS

kubelet

Nodes

Pods

Statefulset

Kubernetes all-nodes

Kubernetes cluster-all

Kubernetes pods-cluster

Kubernetes resources-requests


**Alerts:**

Component Down (API Server, Kubelet, Node exporter, Alertmanager and Prometheus, etc..)

Pod alerts ( Crashloopbackoff, Pending, Not ready)

Workload controller alerts ( Replicas Mismatch, DaemonSet NotScheduled, DaemonSet MisScheduled, Job Failed, and Long-running Jobs)

Resources alerts ( Cpu overcommit, Memory overcommit, Quota exceeded)

Persistent Volume alerts

Kube API error and Client alerts

Prometheus configuration error alerts


**Configure Alertmanager**

While installing the stack, you have to provide alerts receiver details.

image here 

Otherwise, you will never get notified about the cluster state changes and resource utilization.

we can change the configurations as per our interest.

The alert manager is configured with a configuration file written in the YAML format, which defines rules, notification routing, and receivers.
Below are example configurations for Email, Slack and Webhook receiver:

**Slack**

 global:
   resolve_timeout: 5m
   slack_api_url: '< slack_webhook_url >'
 receivers:
 - name: 'slack-notifications'
   slack_configs:
   - channel: '#alerts'
 route:
   group_by:
   - job
   receiver: 'slack-notifications'
   group_interval: 5m
   group_wait: 30s
   repeat_interval: 30m
  
 
  Update configuration as above in the 1-alert manager-configmap.yaml file under manifests directory and apply the configurations.
  
  kubectl apply -f 1-alertmanager-configmap.yaml
  
  **Once configmap is updated, restart the running alert manager pod. A new pod will be created with updated configurations.**
