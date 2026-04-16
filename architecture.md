# 🏗️ Homelab Architecture

```mermaid
graph TD

%% External Access
A[Internet] --> B[Nginx Reverse Proxy]

%% Core Apps
B --> C1[Nextcloud App 1]
B --> C2[Nextcloud App 2]
B --> C3[Nextcloud App 3]

C1 --> D[(PostgreSQL)]
C2 --> D
C3 --> D

C1 --> E[(Redis)]
C2 --> E
C3 --> E

%% Monitoring Stack
F[Prometheus] --> G[Grafana]
F --> H[Alertmanager]

I[Node Exporter] --> F
J[cAdvisor] --> F
K[Blackbox Exporter] --> F

L[Promtail] --> M[Loki]
M --> G

N[Tempo] --> G

%% Extra Services
O[Plex] --> B
P[ERP App] --> B
Q[Uptime Kuma] --> B

%% Networking
R[Tailscale VPN] --> B
