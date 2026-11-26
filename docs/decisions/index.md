# Décisions

Ce dossier explique **pourquoi** j'ai fait chaque choix technique, pour que je puisse les justifier et les revoir plus tard.

## Pourquoi faire un serveur

J'avais besoin d'apprendre et de comprendre comment monter un serveur. Je ne voulais pas faire un homelab juste pour en avoir un : j'ai donc voulu construire quelque chose d'utile tous les jours.

- Un serveur de stockage et de streaming, où je regarde mes films et séries.
- Un serveur d'hébergement, où je peux mettre une page web ou un bot Discord, en faire ce que je veux, et les rendre accessibles de n'importe où.
- Une machine que je peux sécuriser, puis essayer d'attaquer pour m'entraîner et avancer en cybersécurité.

## Format de chaque décision

- **Choix** : ce que j'ai retenu
- **Alternative** : ce que j'ai écarté
- **Pourquoi** : mes raisons
- **Inconvénient** : ce que ce choix me coûte

## Les fichiers

- [Matériel et système](materiel-et-systeme.md) : le PC, Ubuntu Server, Docker
- [Services](services.md) : Jellyfin, la suite *arr, qBittorrent, Vaultwarden, le bot, la page d'accueil
- [Sécurité](securite.md) : UFW, reverse proxy, SSH et Tailscale, Wazuh, compromis sur le téléphone
