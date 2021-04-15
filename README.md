# Synology-Docker-Mediaserver
Working configuration of media services, running Traefik and various other Docker containers on a Synology 218+ NAS

Containers in use:
      - oauth
      - watchtower
      - nzbhydra2
      - organizr
      - sonarr
      - radarr
      - delugevpn
      - sabnzbd
      - bazarr
      - calibre-web
      - jackett
      - tdarr
      - tdarr-node
      - dozzle
      - cert-dumper
      - traefik

Requires docker-compose.yaml and .env file in the same directory, as well as an .ovpn file for those who want to run the Deluge container behind a VPN (see instructions at https://github.com/binhex/arch-delugevpn).

oAuth applied to all containers, with API bypass possible though having created a separate router (see container labels) for oAuth and non-oAuth services.

If you want to connect to non-Docker services, uncomment the relevant "file" provider labels for the Traefik container in docker-compose, and edit the files in the "rules" directory accordingly. The "rules" directory must be nested inside your Traefik config folder on the Synology.
