# 🧩 Self-Hosted Media and Download Stack with Docker Compose

This stack provides a full-featured media automation, downloading, and monitoring system. It uses `docker-compose` and includes tools for movies, TV, music, ROMs, Tidal, WireGuard VPN, and system monitoring.

## 🚀 Services Overview

| Service       | Description                                               | Port / Access URL                    |
|---------------|-----------------------------------------------------------|--------------------------------------|
| Traefik       | Reverse proxy with auto-routing and labels support       | `http://localhost:8888` (dashboard)  |
| WireGuard     | VPN client for secure downloading                        | 51820/UDP                            |
| Transmission  | Torrent client, routed through WireGuard VPN            | Managed via Transmission UI          |
| Radarr        | Movie automation (with Prowlarr + Transmission)          | `http://radarr.nas.docker`           |
| Sonarr        | TV show automation                                       | `http://sonarr.nas.docker`           |
| Lidarr        | Music automation                                         | `http://lidarr.nas.docker`           |
| Prowlarr      | Indexer manager (feeds Sonarr/Radarr/Lidarr)            | `http://prowlarr.nas.docker`         |
| Bazarr        | Subtitles for Radarr and Sonarr                         | `http://bazarr.nas.docker`           |
| FlareSolverr  | Captcha solver for indexers                             | `http://flaresolverr.nas.docker`     |
| Tidarr        | Tidal music downloader + Plex + Gotify                  | `http://tidarr.nas.docker`           |
| RomM          | Retro game ROM manager (local UI)                       | `http://romm.nas.docker`             |
| Glances       | System monitoring dashboard                             | `http://glances.nas.docker`          |
| Portainer Agent | Edge agent for Portainer management UI                | Connects to Portainer remotely       |
| Watchtower    | Auto-update containers + Gotify notifications           | Background                           |

## 🛠️ Setup Instructions

1. **Configure Volumes and Paths**
   Ensure the paths under `/share/CACHEDEV1_DATA/...` exist on your host (e.g., QNAP, NAS, or Linux server).

2. **WireGuard VPN**
   - Edit `wgraoul.conf` with your VPN config.
   - Ensure DNS and routing is correctly configured in `wg0.conf`.

3. **Domain Access**
   Add DNS entries or edit `/etc/hosts` to resolve domains like `radarr.nas.docker`.

4. **Traefik Proxy**
   Traefik routes HTTP requests using labels. Access the dashboard at `http://localhost:8888`.

5. **Secrets and Credentials**
   Replace placeholder values (e.g., `PLEX_TOKEN`, `GOTIFY_TOKEN`, `ADMIN_PASSWORD`) with real values.

6. **Permissions**
   Most containers use `PUID=1000`, `PGID=1000`. Adjust if necessary.

## 🧩 Folder Structure

```
/share/CACHEDEV1_DATA/
├── Container/
│   ├── transmission/
│   ├── radarr/
│   ├── sonarr/
│   ├── romm/
│   └── ...
├── Download/
│   ├── watch/
│   └── complete/
├── Multimedia/
│   ├── Movies/
│   ├── TvShow/
│   └── Music/
```

## 🔐 Security Tips

- Traefik is using `--api.insecure=true`. Do **not expose this stack to the Internet** without hardening (TLS, auth).
- Move credentials to `.env` files or Docker secrets.

## 🔄 Auto-Update System

Watchtower updates containers automatically and notifies you through Gotify.

## 📡 Remote Control

This stack includes Portainer Edge Agent for centralized remote management via Portainer.

## 🕹️ ROM Manager

Use **RomM** to manage your retro game library in `/share/CACHEDEV1_DATA/Container/romm/roms`.

## 📦 Start the Stack

```bash
docker-compose up -d
```

## 🛑 Stop the Stack

```bash
docker-compose down
```

## ✉️ Notifications

Gotify integration sends updates from Tidarr and Watchtower to your preferred device.

## 📚 Credits

- [LinuxServer.io](https://www.linuxserver.io/)
- [rommapp/romm](https://github.com/rommapp/romm)
- [cstaelen/tidarr](https://github.com/cstaelen/tidarr)
- [Traefik Labs](https://traefik.io/)
- [containrrr/watchtower](https://containrrr.dev/watchtower/)
