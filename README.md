# Synology-Docker-Mediaserver
Working configuration of media services, running Linuxserver Swag for reverse proxy, and various other Docker containers, on a Synology 218+ NAS.

Router ports forwarded to NAS:
Plex (32400 is default); Http 81 (external) > 81 (internal, only needed if running Swag dashboard); Https: 443 (external) > 449 (internal)

Containers in use:
      - swag
      - watchtower
      - prowlarr
      - organizr
      - sonarr
      - radarr
      - qbittorrent
      - sabnzbd
      - bazarr
      - calibre-web
      - calibre
      - readarr
      - dozzle
      - cloudflare-ddns
      - lidarr
      - recyclarr
      - plex
      - tautulli
      - tdarr
      - vaultwarden (self-hosted Bitwarden)

Requires docker-compose.yaml and .env file in the same directory.

Auth is applied to all containers via Organizr, with API bypass, using swag/nginx/proxy-conf edits for each service (in the location block) as follows. To allow API access (e.g. for NZB360), don't add this to the API block.

        include /config/nginx/proxy-confs/organizr-auth.subfolder.conf;
        auth_request /auth-4;
