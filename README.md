# Synology-Docker-Mediaserver
Working configuration of media services, running Traefik and various other Docker containers on a Synology 218+ NAS

Containers in use:
      - oauth
      - watchtower
      - nzbhydra2
      - organizr
      - sonarr
      - radarr
      - deluge
      - sabnzbd
      - bazarr
      - calibre-web
      - jackett
      - tdarr
      - tdarr-node
      - dozzle
      - cert-dumper
      - traefik
      - vaultwarden (self-hosted Bitwarden)

Requires docker-compose.yaml and .env file in the same directory.

oAuth is applied to all containers, with API bypass possible though having created a separate router (see container labels) for oAuth and non-oAuth services.

The "rules" directory must be nested inside your Traefik config folder on the Synology.
