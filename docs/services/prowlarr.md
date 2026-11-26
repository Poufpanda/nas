# Prowlarr

## À quoi ça sert
Prowlarr centralise les sources de recherche (indexeurs) à un seul endroit. Je les configure une fois dans Prowlarr, et il les partage automatiquement avec Radarr et Sonarr, au lieu de devoir les ajouter dans chacun.

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 9696
- Connecté a nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur 'prowlarr'
- Accessible via : https://prowlarr.mondomaine.duckdns.org

## Données et configuration
- Configuration : `/prowlarr/config`

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS avec nginx
- Protections particulières : compte avec mot de passe fort, conteneur non joignable directement

## Problèmes rencontrés
- Problemes du au fait que les indexers n'etaient pas disponibles
- Mauvaise configuration du service, path incorrect dans mon docker compose
