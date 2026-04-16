# 🏗️ Homelab Architecture

```mermaid
graph TD

%% External Access
A[Internet] --> B[Cloudflare Tunnel]

%% Nextcloud via Nginx LB
B --> C[Nginx Load Balancer]
C --> D1[Nextcloud App 1]
C --> D2[Nextcloud App 2]
C --> D3[Nextcloud App 3]

D1 --> E[(PostgreSQL)]
D2 --> E
D3 --> E

D1 --> F[(Redis)]
D2 --> F
D3 --> F

%% Other Services (Direct via Tunnel)
B --> G[Grafana]
B --> H[Prometheus]
B --> I[Uptime Kuma]
B --> J[ERP App]

%% Monitoring Stack
H --> G
H --> K[Alertmanager]

L[Node Exporter] --> H
M[cAdvisor] --> H
N[Blackbox Exporter] --> H

O[Promtail] --> P[Loki]
P --> G

Q[Tempo] --> G

%% Private Network (Tailscale)
R[Tailscale VPN] --> D1
R --> D2
R --> D3
R --> G
R --> H
R --> J

%% Backup Servers
R --> S[Backup Server 1]
R --> T[Backup Server 2]
