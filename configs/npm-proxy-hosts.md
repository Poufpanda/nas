# Reverse proxy : hôtes configurés

Le reverse proxy (Nginx Proxy Manager) garde sa configuration dans sa propre base de données, pas dans des fichiers nginx à écrire à la main. Ce tableau décrit ce que j'ai configuré dans son interface, pour pouvoir le refaire.

Réglages communs à tous les hôtes :
- Schéma : `http` (le chiffrement est géré par le proxy, le trafic reste dans le réseau Docker)
- Onglet SSL : certificat Let's Encrypt, **Force SSL** activé, **HTTP/2** activé
- Les conteneurs sont joints par leur nom, sur le réseau Docker `proxy`

| Domaine | Conteneur cible | Port | Websockets |
|---|---|---|---|
| `<mon-domaine>` | homepage | 80 | non |
| `jellyfin.<mon-domaine>` | jellyfin | 8096 | oui |
| `vaultwarden.<mon-domaine>` | vaultwarden | 80 | oui |
| `qbittorrent.<mon-domaine>` | qbittorrent | 8080 | non |
| `radarr.<mon-domaine>` | radarr | 7878 | oui |
| `sonarr.<mon-domaine>` | sonarr | 8989 | oui |
| `prowlarr.<mon-domaine>` | prowlarr | 9696 | oui |

*(À vérifier : que chaque ligne correspond à mes réglages réels, notamment le domaine de Prowlarr.)*

## Améliorations prévues

- Restreindre l'accès aux interfaces d'administration (Radarr, Sonarr, Prowlarr, qBittorrent) à Tailscale ou à une liste d'adresses autorisées, avec une « Access List » de Nginx Proxy Manager.
- Ajouter l'en-tête HSTS sur les hôtes sensibles, Vaultwarden en priorité.
