# Docker wireguard torrent stack
Docker stack for Prowlarr, Radarr, Sonarr, Lidarr, Gotify using Transmission with Wireguard & Tidal DL.

## Services
- **traefik**: http://traefik.nas.docker
- **transmission**: http://transmission.nas.docker:9091
- **radarr**: http://radarr.nas.docker
- **sonarr**: http://sonarr.nas.docker
- **lidarr**: http://lidarr.nas.docker
- **prowlarr**: http://prowlarr.nas.docker
- **glances**: http://glances.nas.docker
- **flaresolver**
- **watchtower**
- **portainer-agent**

## Volumes folder structure
- **/share/CACHEDEV1_DATA/Container**: Used to store container config data

- **/share/CACHEDEV1_DATA/Download**: Path to `transmission` download folders.
- **/share/CACHEDEV1_DATA/Download/complete**: Path to `transmission` completed download folders.
- **/share/CACHEDEV1_DATA/Download/watch**: Path to `transmission` folder to monitor for new media files.

- **/share/CACHEDEV1_DATA/Multimedia/Movies**: This volume is used by the `radarr` service to access the movie library.
- **/share/CACHEDEV1_DATA/Multimedia/TvShow**: This volume is used by the `sonarr` service to access the TV show library.
- **/share/CACHEDEV1_DATA/Multimedia/Music**: This volume is used by the `lidarr` service to access the TV show library.

## Doc
- **traefik**: https://doc.traefik.io/traefik/getting-started/quick-start/
- **transmission**: https://github.com/linuxserver/docker-transmission
- **radarr**: https://github.com/linuxserver/docker-radarr
- **sonarr**: https://github.com/linuxserver/docker-sonarr
- **lidarr**: https://hub.docker.com/r/linuxserver/lidarr
- **prowlarr**: https://github.com/linuxserver/docker-prowlarr
- **overseer**: https://hub.docker.com/r/linuxserver/overseerr
- **gotify**: https://gotify.net/docs/install
