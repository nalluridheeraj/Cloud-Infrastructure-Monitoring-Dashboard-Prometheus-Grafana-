# Cloud Monitoring Dashboard (Prometheus + Grafana)

## Architecture Diagram
<img width="1536" height="1024" alt="architecture" src="https://github.com/user-attachments/assets/cbca64b2-d2fe-4f14-b6f7-8d2fc231b1a8" />

## Problem Statement
Monitoring system performance manually is inefficient and error-prone.  
This project builds an automated monitoring and alerting system for cloud infrastructure.

---

## Overview

This project implements a real-time cloud monitoring system using Prometheus and Grafana on an AWS EC2 instance.

It continuously collects system metrics (CPU, memory, disk, network) using Node Exporter, stores them in Prometheus, and visualizes them through Grafana dashboards.

An alerting mechanism is configured to notify via email when CPU usage exceeds 80%.

This setup closely simulates real-world SRE/DevOps monitoring systems used in production environments.

---

## Features

- Real-time system monitoring (CPU, Memory, Disk, Network)
- Custom Grafana dashboards
- Alerting system for high CPU usage (>80%)
- Prometheus time-series data storage
- Scalable monitoring architecture

---

## Tech Stack

- Prometheus (Monitoring & Metrics Storage)
- Grafana (Visualization & Alerting)
- Node Exporter (System Metrics Collection)
- AWS EC2 (Cloud Infrastructure)
- Linux (Ubuntu)
- Bash (Setup & Configuration)

---

## Architecture Explanation

1. Node Exporter runs on the EC2 instance and exposes system metrics on port 9100  
2. Prometheus scrapes these metrics at regular intervals and stores them  
3. Grafana connects to Prometheus as a data source  
4. Dashboards visualize real-time system performance  
5. Alerts are triggered when thresholds (e.g., CPU > 80%) are breached  

---

## PromQL Queries Used

### CPU Usage

100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[1m])) * 100)

### Memory Usage

(node_memory_MemTotal_bytes - node_memory_MemAvailable_bytes) / node_memory_MemTotal_bytes * 100

### Disk Usage

(node_filesystem_size_bytes - node_filesystem_free_bytes) / node_filesystem_size_bytes * 100

---

## Alerting

- Condition: CPU usage > 80%
- Notification: Email alert
- Message: "Hey, your CPU usage has just crossed 80% 🚨"

---

## Future Improvements

- Add Slack/Discord alert integration
- Monitor multiple servers
- Add container monitoring (Docker/Kubernetes)


## PromQL Queries Used

### CPU Usage
