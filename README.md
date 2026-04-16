# 🧱 DevOps Homelab Infrastructure

## 📌 Overview

Production-like self-hosted infrastructure running multiple services using Docker.

---

## 🏗️ Architecture

### Core Applications
- Nextcloud (3-instance cluster)
- PostgreSQL databases
- Redis caching
- Nginx load balancer

### Observability Stack
- Prometheus (metrics collection)
- Grafana (dashboards)
- Alertmanager (alerting)
- Loki + Promtail (logging)
- Tempo (distributed tracing)
- Node Exporter + cAdvisor (system metrics)
- Blackbox exporter (endpoint monitoring)

### Networking & Access
- Tailscale (private VPN access)
- Reverse proxy (Nginx)

### Additional Services
- Plex media server
- Uptime Kuma (service monitoring)
- Watchtower (auto container updates)
- Custom ERP system

---

## 🔥 Key Highlights

- Managed 20+ running containers
- Built full observability pipeline (metrics + logs + traces)
- Implemented service monitoring and alerting
- Designed multi-service architecture with secure access
- Automated container updates using Watchtower

---

## 📦 Running Services (Live Stack)

Current infrastructure runs 20+ containers including:

### 🧱 Core Applications
- Nextcloud cluster (3 instances + Nginx load balancer)
- PostgreSQL databases
- Redis cache
- Collabora (document editing)

### 📊 Observability Stack
- Prometheus
- Grafana
- Alertmanager
- Loki + Promtail
- Tempo (tracing)
- Node Exporter, cAdvisor, Blackbox Exporter

### 🌐 Access & Networking
- Cloudflare Tunnel (Zero Trust ingress)
- Tailscale (private VPN network)

### 🧰 Additional Services
- Uptime Kuma (status monitoring)
- Watchtower (auto updates)
- Plex (media server)
- Custom ERP system

---

## 🚀 Example Services

```bash
docker ps
