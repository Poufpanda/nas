# Jellyfin

## À quoi ça sert
Jellyfin permet d'accéder à du contenu multimédia (films, séries) stocké sur mon serveur, depuis n'importe quel appareil.

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Port interne : 8096 (Ce service est connecte maintenant grace a un reseau local nginx et accessible via son nom de container soit jellyfin)
- Accessible via : https://jellyfin.mondomaine.duckdns.org

## Données et configuration
- Les fichiers sont stockes sur un fichier a part (/media)
- Chaque type de contenu a son propre fichier (/media/films | /media/series)
- Un dossier de configuration (/config) avec les comptes Jellyfin stockes, les metadonnees, etc
- Fichier sauvegarde : /config

## Sécurité
- Exposé sur Internet : oui
- Protections particulières : HTTPS via nginx, pas d'inscription ouverte, un compte admin, et un autre pour tous les jours les deux avec des mots de passe forts
- Fichier /media en lecture seule

## Problèmes rencontrés
- Pour l'instant je n'ai pas rencontre de probleme avec ce service
