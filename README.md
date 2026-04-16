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

## 🚀 Example Services

```bash
docker ps
