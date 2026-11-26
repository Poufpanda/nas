# QBitTorrent

## À quoi ça sert
QBitTorrent recoit des liens de torrent a telecharger, puis les range dans `/media/downloads`

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 8080
- Connecté a nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur 'qbittorrent'
- Accessible via : https://qbittorrent.mondomaine.duckdns.org

## Données et configuration
- Configuration : `/qbittorrent/config`
- Media : `/media/downloads`

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS avec nginx
- Protections particulières : compte avec mot de passe fort, conteneur non joignable directement

## Problèmes rencontrés
- Problemes lies aux etiquettes, radarr et sonarr
- Service inutilisable suite a la mauvaise configuration du service
