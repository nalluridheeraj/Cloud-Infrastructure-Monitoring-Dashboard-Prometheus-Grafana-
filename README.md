# Cloud Monitoring Dashboard (Prometheus + Grafana)

## Overview

Built a monitoring system on AWS EC2 using Prometheus and Grafana.

## Features

* CPU, Memory, Disk monitoring
* Custom dashboards
* Alert when CPU > 80%

## Tech Used

* Prometheus
* Grafana
* Node Exporter
* AWS EC2
* Linux (Ubuntu)
* Bash

## Architecture

Node Exporter → Prometheus → Grafana

## Queries Used

CPU:
100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[1m])) * 100)

Memory:
(node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / node_memory_MemTotal_bytes * 100

Disk:
(node_filesystem_size_bytes - node_filesystem_free_bytes) / node_filesystem_size_bytes * 100
