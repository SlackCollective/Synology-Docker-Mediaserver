# Synology-Docker-Mediaserver
Working configuration of media services, running Linuxserver Swag for reverse proxy, and various other Docker containers, on a Synology 218+ NAS.

Router ports forwarded to NAS:
Plex (32400 is default); Https: 443 (external) > 449 (internal)

Containers in use:
      - swag
      - prowlarr
      - organizr
      - sonarr
      - radarr
      - qbittorrent
      - qbit-manage
      - sabnzbd
      - bazarr
      - calibre
      - dozzle
      - cloudflare-ddns
      - plex
      - tautulli
      - tdarr
      - notifiarr
      - vaultwarden (self-hosted Bitwarden)

Requires docker-compose.yaml and .env file in the same directory.

Auth is applied to containers via Organizr, with API bypass, using swag/nginx/proxy-conf edits for each service (in the location block) as follows. To allow API access (e.g. for NZB360), don't add this to the API block.

        include /config/nginx/proxy-confs/organizr-auth.subfolder.conf; #applicable even if using subdomains rather than subfolders
        auth_request /auth-4; #auth-4 is a particular user role, you might want to use a different one
