# Radarr

## À quoi ça sert
Radarr gère ma collection de films. Je lui indique les films que je veux (ma « liste de souhaits »), il les recherche automatiquement, les envoie à qBittorrent pour le téléchargement, puis les renomme et les range dans `/media/films`, où Jellyfin les retrouve.

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 7878
- Connecté a nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur 'radarr'
- Accessible via : https://radarr.mondomaine.duckdns.org

## Données et configuration
- Configuration : `/radarr/config`
- Media : `/media/films`
- Acces : `/media/downloads`

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS avec nginx
- Protections particulières : compte avec mot de passe fort, conteneur non joignable directement

## Problèmes rencontrés
- Films non visible suite au telechargement via un lien magnet sans passer par radarr : ajout de l'etiquette TV-radarr dans QBitTorrent
- Service inutilisable suite a la mauvaise configuration avec prowlarr
