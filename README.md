# Homelab

Serveur personnel auto-hébergé, monté sur un ancien PC que je n'utilisais plus. Il me sert au quotidien de serveur multimédia, d'hébergeur de serveurs de jeu et de plateforme pour déployer mes propres scripts et pages web, que je contrôle de bout en bout.

## Vue d'ensemble

- **Multimédia** : Jellyfin, avec Radarr, Sonarr, Prowlarr et qBittorrent pour la gestion de la bibliothèque.
- **Jeu** : hébergement de serveurs Minecraft.
- **Web et scripts** : mise en ligne de scripts et de pages web, avec un contrôle total sur l'environnement.
- **Accès** : le serveur est accessible depuis n'importe où, en HTTPS, derrière un reverse proxy.
- **Évolutif** : la page d'accueil (présentation type CV) sert de base pour héberger par la suite les applications que je développe.

## Services

| Service | Rôle |
|---|---|
| Jellyfin | Serveur multimédia |
| Radarr | Gestion et automatisation des films |
| Sonarr | Gestion et automatisation des séries |
| Prowlarr | Gestionnaire d'indexeurs pour Radarr et Sonarr |
| qBittorrent | Client de téléchargement |
| Vaultwarden | Gestionnaire de mots de passe auto-hébergé |
| Nginx (reverse proxy) | Point d'entrée unique, terminaison TLS |
| Serveurs Minecraft | Hébergement de parties |
| Page d'accueil | Vitrine statique (HTML/CSS), servie par un conteneur `nginx:alpine` |

Les services tournent dans des conteneurs Docker.

## Documentation

- [Architecture](architecture.md) : matériel, choix techniques et réseau
- [Sécurité](security.md) : mesures de protection, accès distant, limites

## Objectifs

- Apprendre l'administration système et la sécurisation d'un serveur exposé sur Internet.
- Disposer d'une base d'hébergement que je maîtrise pour mes propres projets.
- Documenter chaque choix pour pouvoir le justifier et le reproduire.
