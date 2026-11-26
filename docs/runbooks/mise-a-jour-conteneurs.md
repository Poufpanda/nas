# Mettre à jour les conteneurs Docker

**Quand l'utiliser** : une fois par mois, ou quand une faille est annoncée sur un service.
**Pré-requis** : accès au serveur (en local ou via Tailscale).

## Avant de commencer
1. Sauvegarder la configuration du service concerné (copie du dossier `/<service>/config`).
2. Pour Vaultwarden : faire d'abord la sauvegarde complète.
3. Noter la version actuelle de l'image, pour pouvoir revenir en arrière :
   `docker ps --format "table {{.Names}}\t{{.Image}}"`

## Étapes (un service à la fois)
1. Aller dans le dossier du service :
   `cd ~/docker/<service>`
2. Télécharger la nouvelle image :
   `docker compose pull`
3. Relancer le conteneur avec la nouvelle image :
   `docker compose up -d`
4. Nettoyer les anciennes images, une fois que tout fonctionne :
   `docker image prune`

## Vérifier que ça a marché
- Le conteneur tourne : `docker ps` (statut « Up »)
- Pas d'erreur dans les logs : `docker compose logs --tail 50`
- Le service répond : ouvrir son adresse dans le navigateur et se connecter

## Si ça ne marche pas : revenir en arrière
1. Dans `docker-compose.yml`, remplacer `image: nom:latest` par la version notée avant (ex. `nom:1.2.3`).
2. `docker compose up -d`
3. Restaurer la configuration sauvegardée si le service refuse de démarrer
   (les mises à jour de Sonarr/Radarr/Prowlarr peuvent modifier leur base de données).

## Remarques
- Ne jamais mettre à jour tous les services d'un coup : si quelque chose casse, on ne sait plus quoi.
- Commencer par les services peu critiques (Jellyfin) avant Vaultwarden.
