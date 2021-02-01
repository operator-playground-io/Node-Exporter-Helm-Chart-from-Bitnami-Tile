                                                     What is Node Exporter
                                                            

The node exporter can read system-level statistics about bare-metal nodes or virtual machines and export them for Prometheus. Using a DaemonSet, Kubernetes can run one node exporter per cluster node, and expose the node exporter as a service.

Node Exporter is a PromeWhat is Prometheus
Prometheus is an open-source system for monitoring and alerting tool. It is developed in the GO language. Prometheus tool is currently a standalone open source project and maintained independently by any organization. You can check more details here.


### What is Kube-state-metrics?

kube-state-metrics is a simple service that listens to the Kubernetes API server and generates metrics about the state of the objects.It is not focused on the health of the individual Kubernetes components, but rather on the health of the various objects inside, such as deployments, nodes and pods.

The metrics are exported through the Prometheus golang client on the HTTP endpoint /metrics on the listening port (default 80). They are served either as plaintext or protobuf depending on the Accept header. They are designed to be consumed either by Prometheus itself or by a scraper that is compatible with scraping a Prometheus client endpoint. You can also open /metrics in a browser to see the raw metrics.

**Why Prometheus Monitoring?**

Open-source and of course freely available 🙂

It is constantly contributed by the community.

It is stable and used by many good brands.

Good community support and well documented. 

You do not need any big infrastructure to get started. 

It can be started with 1 GB RAM.

Prometheus Grafana: While Prometheus has its own UI to check any metrics. But, many prefer Grafana with Prometheus which gives you better visualization on your Prometheus metrics. 

Lots of pre-build Grafana dashboard and exporters already written. 

You have to just reuse those exporters.

You can check the list of Prometheus features here.

**Prerequisites for setting up Prometheus monitoring**


2 GB RAM

10 GB Avg local disk storage.

GOLANG (go1.11.5 linux/amd64)

Centos7 RHEL


**Object of the tutorial**

1- What is Node-Exporter?

2- Waht is Node Exporter hem chart from Bitnami?

3-Why Prometheus Monitoring?

4-What is Kube-state-metrics?

5-Prerequisites for setting up Prometheus monitoring




