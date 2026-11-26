# Jellyfin

## À quoi ça sert
Jellyfin permet d'accéder à mes films et séries stockés sur le serveur, depuis n'importe quel appareil.

## Installation
- Lancé avec Docker ([docker-compose.yml](../compose/jellyfin/docker-compose.yml))
- Port interne : 8096, non publié sur l'hôte
- Connecté à nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur `jellyfin`
- Accessible via : https://jellyfin.mon-domaine.duckdns.org

## Données et configuration
- Médias : `/media/films` et `/media/series`
- Configuration de Jellyfin : (/jellyfin/config)
- À sauvegarder : la configuration (les médias sont remplaçables)

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS via nginx
- Protections : comptes Jellyfin avec mots de passe forts, conteneur non joignable directement

## Problèmes rencontrés
- Medias non visible du a une mauvaise configuration du chemin dans le docker
- Service lent : mise en place d'un transcodage plus fort utilisant la carte graphique

## Améliorations
- Mise en place de plugins de QoL
