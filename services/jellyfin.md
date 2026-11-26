# Jellyfin

## Permet d'acceder a du contenu multimedia stockes sur un serveur

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 8096 (Ce service est connecte maintenant grace a un reseau local nginx et accessible via son nom de container soit jellyfin)
- Accessible via : https://jellyfin.jaimelesfilms.duckdns.org

## Données et configuration
- Les fichiers sont stockes sur un fichier a part (/media)
- Chaque type de contenu a son propre fichier (/media/films | /media/series)

## Sécurité
- Exposé sur Internet : oui
- Protections particulières : comptes Jellyfin, nginx

## Problèmes rencontrés
- Pour l'instant je n'ai pas rencontre de probleme avec ce service
