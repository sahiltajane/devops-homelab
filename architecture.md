# 🏗️ Homelab Architecture (Production + DNS Accurate)

```mermaid
flowchart TD

%% =========================
%% INTERNET + DNS
%% =========================
USER[Users] --> DNS[Cloudflare DNS]

DNS --> CF[Cloudflare Tunnel]

%% =========================
%% INGRESS ROUTING
%% =========================
CF --> NC_DOMAIN[cloud.tsginfotech.co.in]
CF --> ERP_DOMAIN[report.tsginfotech.co.in]
CF --> STATUS_DOMAIN[status.tsginfotech.co.in]
CF --> GRAF_DOMAIN[dash.tsginfotech.co.in]
CF --> PLEX_DOMAIN[plex.tsginfotech.co.in]

%% =========================
%% LOCAL SERVICES (PORT BASED)
%% =========================
NC_DOMAIN --> LB[Nginx LB :8080]
ERP_DOMAIN --> ERP[ERP App :8900]
STATUS_DOMAIN --> UP[Uptime Kuma :3001]
GRAF_DOMAIN --> GRAF[Grafana :3000]
PLEX_DOMAIN --> PLEX[Plex :32400]

%% =========================
%% NEXTCLOUD NETWORK
%% =========================
subgraph nextcloud_default

LB --> NC1[Nextcloud App 1]
LB --> NC2[Nextcloud App 2]
LB --> NC3[Nextcloud App 3]

NC1 --> DB[(Postgres)]
NC2 --> DB
NC3 --> DB

NC1 --> REDIS[(Redis)]
NC2 --> REDIS
NC3 --> REDIS

COL[Collabora :9980] --> NC1
COL --> NC2
COL --> NC3

end

%% =========================
%% MONITORING NETWORK
%% =========================
subgraph monitoring_default

PROM[Prometheus]

NODE[Node Exporter]
CAD[cAdvisor]
BB[Blackbox]

NODE --> PROM
CAD --> PROM
BB --> PROM

PROM --> GRAF
PROM --> ALERT[Alertmanager]

PROMTAIL --> LOKI
LOKI --> GRAF

TEMPO --> GRAF

PUSH --> PROM

end

%% =========================
%% ERP NETWORK
%% =========================
subgraph test_default

ERP --> ERPDB[(Postgres)]

end

%% =========================
%% PRIVATE NETWORK
%% =========================
TS[Tailscale VPN]

TS --> NC1
TS --> NC2
TS --> NC3
TS --> DB
TS --> GRAF
TS --> ERP

TS --> B1[Backup Server 1]
TS --> B2[Backup Server 2]
