# Décisions : services

## Pourquoi Jellyfin
- **Choix** : Jellyfin comme serveur multimédia.
- **Alternative** : Plex.
- **Pourquoi** : Jellyfin est open source, très personnalisable, et ne demande pas de compte externe : tout reste sur mon serveur. Plex n'est pas open source.
- **Inconvénient** : moins répandu et moins poli que Plex sur certaines applications.

## Pourquoi la suite *arr (Radarr, Sonarr, Prowlarr)
- **Choix** : Radarr, Sonarr et Prowlarr.
- **Alternative** : chercher, télécharger et ranger chaque fichier à la main.
- **Pourquoi** : ils s'intègrent facilement entre eux et avec Jellyfin, et ils automatisent la recherche, le suivi des nouveaux épisodes, le renommage et le rangement. Je n'ai pas comparé d'autres outils.
- **Inconvénient** : beaucoup de réglages entre les services, source de plusieurs de mes problèmes de configuration (voir les runbooks).

## Pourquoi qBittorrent
- **Choix** : qBittorrent comme client de téléchargement.
- **Alternative** : d'autres clients de torrent.
- **Pourquoi** : open source, très utilisé, mis à jour régulièrement, et disponible avec une interface web adaptée à Docker.
- **Inconvénient** : son interface web est un service d'administration à protéger (voir [securite.md](securite.md)).

## Pourquoi Vaultwarden
- **Choix** : Vaultwarden plutôt que Bitwarden auto-hébergé.
- **Alternative** : le serveur Bitwarden officiel.
- **Pourquoi** : j'ai essayé d'installer Bitwarden, mais je n'ai pas réussi à écrire un `docker-compose` qui fonctionne. Sa version officielle est plus lourde (plusieurs conteneurs). Vaultwarden est une version légère et open source, compatible avec les applications et extensions Bitwarden.
- **Inconvénient** : ce n'est pas le produit officiel, donc moins de garanties de support.

## Pourquoi un bot en Python
- **Choix** : un bot Python relié à Wazuh, avec Discord comme canal de messages.
- **Alternative** : consulter les alertes à la main dans Wazuh.
- **Pourquoi** : Python est facile à intégrer, et je connaissais déjà les bases d'un bot Discord. Le bot m'alerte même quand je ne regarde pas Wazuh, et me permet de vérifier l'état du serveur à distance.
- **Inconvénient** : un composant de plus à maintenir et à protéger (token, accès à Docker).

## Pourquoi une page d'accueil en HTML/CSS pur
- **Choix** : une page statique, servie par un conteneur `nginx:alpine`.
- **Alternative** : un framework (React, PHP...).
- **Pourquoi** : simple à écrire et à maintenir, et très peu de surface d'attaque : pas de base de données ni de formulaire.
- **Inconvénient** : le contenu se met à jour à la main, rien n'est dynamique.
