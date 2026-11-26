
# Architecture

## Contexte et choix du matériel

Je disposais de plusieurs PC inutilisés à la maison et j'ai d'abord essayé de tous les transformer en serveurs. Cela n'a pas fonctionné : chacun avait un disque dur défaillant.

Les disques neufs étant trop chers pour ce projet, je me suis tourné vers l'occasion. J'ai trouvé une annonce pour un PC portable fonctionnel équipé d'un HDD de 1 To, et j'ai remplacé le disque défaillant de l'une de mes machines par celui-ci. Depuis, le serveur fonctionne de manière stable.

## Matériel

| Élément | Détail |
|---|---|
| Machine | HP Omen 15 (2015) |
| Stockage | HDD 1 To (seconde main) |
| Réseau | Ethernet, relié directement à la box |
| Rôle | Serveur 24/7 |

C'est la machine la plus performante parmi toutes celles dont je disposais, ce qui en fait un bon candidat malgré son âge.

## Logiciel

- Les services sont déployés avec **Docker** (un conteneur par service).
- Un **reverse proxy nginx** est le point d'entrée unique et gère les certificats TLS.
- Les ports non nécessaires sont fermés par le pare-feu (voir [security.md](security.md)).

## Réseau

```
Internet
   │
Box (IPv4 fixe) ──► Pare-feu UFW (ports minimaux)
                        │
                  Reverse proxy nginx (HTTPS / TLS)
                        │
        ┌───────────────┼───────────────┐
     Jellyfin     Vaultwarden      Page d'accueil ...
   (+ Radarr, Sonarr, Prowlarr, qBittorrent, serveurs Minecraft)
```

L'accès d'administration se fait en local ou via Tailscale (aucun port SSH n'est exposé sur Internet).

## Pistes d'amélioration

- Ajouter un second disque ou une sauvegarde externe : un seul HDD d'occasion reste un point de défaillance unique.
- Ajouter ici un schéma réseau plus détaillé et la liste des conteneurs (`docker ps`).
