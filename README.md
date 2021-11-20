# Synology-Docker-Mediaserver
Working configuration of media services, running Linuxserver Swag for reverse proxy, and various other Docker containers, on a Synology 218+ NAS

Containers in use:
      - watchtower
      - prowlarr
      - organizr
      - sonarr
      - radarr
      - deluge
      - sabnzbd
      - bazarr
      - calibre-web
      - calibre
      - readarr
      - tdarr
      - tdarr-node
      - dozzle
      - cloudflare-ddns
      - lidarr
      - vaultwarden (self-hosted Bitwarden)

Requires docker-compose.yaml and .env file in the same directory.

Auth is applied to all containers via Organizr, with API bypass, using swag/nginx/proxy-conf edits for each service as follows:
        include /config/nginx/proxy-confs/organizr-auth.subfolder.conf;
        auth_request /auth-4;
