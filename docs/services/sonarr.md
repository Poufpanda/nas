# Sonarr

## À quoi ça sert
Sonarr gère ma collection de séries. Je lui indique les séries que je veux suivre, il surveille la sortie des nouveaux épisodes, les envoie à qBittorrent pour le téléchargement, puis les renomme et les range dans `/media/series`, où Jellyfin les retrouve.

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 8989
- Connecté a nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur 'sonarr'
- Accessible via : https://sonarr.mondomaine.duckdns.org

## Données et configuration
- Configuration : `/sonarr/config`
- Media : `/media/series`
- Acces : `/media/downloads`

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS avec nginx
- Protections particulières : compte avec mot de passe fort, conteneur non joignable directement

## Problèmes rencontrés
- Series non visibles suite au telechargement via un lien magnet sans passer par sonarr : ajout de l'etiquette Serie dans QBitTorrent
