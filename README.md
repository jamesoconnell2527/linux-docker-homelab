# linux-docker-homelab

A collection of Docker Compose configurations for self-hosted services running on my home Linux server. Each service lives in its own subfolder with its own `docker-compose.yml` and environment configuration.

## Structure

```
docker/
├── immich/       # Self-hosted photo and video management
├── jellyfin/     # Media server for movies, TV, and music
├── grafana/      # Monitoring stack (Prometheus + Grafana + Node Exporter)
└── tailscale/    # Mesh VPN for secure remote access
```

## Services

### Immich
Self-hosted alternative to Google Photos. Runs the Immich server, machine learning service, Redis, and a Postgres database with vector search support.

### Jellyfin
Open-source media server for streaming movies, TV shows, and music from local storage.

### Grafana + Prometheus
Monitoring stack for the server itself:
- **Prometheus** — metrics collection
- **Node Exporter** — host-level system metrics
- **Grafana** — dashboards and visualization

### Tailscale
Provides secure, private remote access to this server and its services over a mesh VPN, without exposing ports directly to the internet.

## Setup

Each service directory contains its own `docker-compose.yml`. To bring a service up:

```bash
cd <service-folder>
docker compose up -d
```

### Environment variables

Sensitive values (database passwords, auth keys, etc.) are **not** committed to this repo. Each service that requires secrets expects a local `.env` file in its own folder, which is excluded via `.gitignore`.

