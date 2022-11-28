---
title: "prom@home - Part 1 - Prometheus, Grafana, & Kubernetes"
date: 2020-11-01
draft: false
---

## prom@home

This post is the first in a series of posts explaining how to setup a home monitoring platform based on Prometheus & Kubernetes. The aim is to build a customizable monitoring platform with a Grafana dashboard displaying information about your home.

### Suggested Reading

This guide uses Prometheus, Grafana, and Kubernetes. These are complicated technologies, but you do not need to fully understand them in order to build things out of them. Some background knowledge is useful though.

- [Prometheus Overview](https://prometheus.io/docs/introduction/overview)
- [Prometheus: Up & Running, _Brian Brazil_](https://www.oreilly.com/library/view/prometheus-up/9781492034131/ch01.html)
- [Kubernetes The Hard Way, _Kelsey Hightower_](https://github.com/kelseyhightower/kubernetes-the-hard-way)
- [Introduction to Grafana](https://grafana.com/docs/grafana/latest/introduction/)

### Initial Setup

The first step is to get a Linux system with Kubernetes installed. I recommend using [k3d](https://k3d.io/v5.4.6/) on something like an [Intel NUC](https://www.amazon.com/intel-nuc/s?k=intel+nuc). Follow the [k3d Quick Start](https://k3d.io/v5.4.6/#quick-start) guide to get a cluster up and running. 

After you have a k3d cluster running, install Helm, Prometheus, & Grafana:

```
# install helm
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# install prometheus
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/prometheus

# install grafana
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install grafana grafana/grafana
```	

