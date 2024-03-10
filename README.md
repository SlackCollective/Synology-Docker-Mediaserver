# Synology-Docker-Mediaserver
Working configuration of media services, running Linuxserver Swag for reverse proxy, and various other Docker containers, on a Synology 218+ NAS.

Router ports forwarded to NAS:
Plex (32400 is default); Https: 443 (external) > 449 (internal). Also 80 (external) > 89 (internal) if you want to be able to redirect all web traffic to https.

# Containers in use:
### WEBSERVER/REVERSE PROXY/DNS/VPN
* swag
* cloudflare-ddns
* gluetun
### FRONTEND/AUTH
* organizr
### INDEXERS
* prowlarr
### DOWNLOADERS
* sabnzbd
* qbittorrent
* qbit-manage
* autobrr
* omegabrr
### MEDIA SEARCH
* sonarr
* radarr
### VIDEO CONVERSION
* tdarr
### HOME THEATRE
* plex
* tautulli
### BOOKS
* calibre
### PASSWORD MANAGEMENT
* vaultwarden (self-hosted Bitwarden)
### SYSTEM MONITORING
* deunhealth
* dozzle
* notifiarr

Requires docker-compose.yaml and .env file in the same directory.

Auth is applied to containers via Organizr, with API bypass, using swag/nginx/proxy-conf edits for each service (in the location block) as follows. To allow API access (e.g. for NZB360), don't add this to the API block.

        include /config/nginx/proxy-confs/organizr-auth.subfolder.conf; #applicable even if using subdomains rather than subfolders
        auth_request /auth-4; #auth-4 is a particular user role, you might want to use a different one
