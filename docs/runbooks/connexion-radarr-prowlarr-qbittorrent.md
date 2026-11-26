# Problèmes de connexion entre Prowlarr, Radarr, Sonarr et qBittorrent

**Quand l'utiliser** : Radarr ou Sonarr ne trouvent rien, un indexeur est signalé indisponible, ou un service n'arrive plus à joindre un autre (message d'erreur rouge dans l'interface, bouton « Test » en échec).
**Pré-requis** : accès aux interfaces web des services et au dossier des `docker-compose.yml`.

## Principe
Les services se parlent entre eux à travers le réseau Docker partagé. Chaque lien a une adresse et une clé ou un identifiant à vérifier :

- Prowlarr → Radarr / Sonarr (pour partager les indexeurs)
- Radarr / Sonarr → Prowlarr (pour rechercher)
- Radarr / Sonarr → qBittorrent (pour télécharger)

## Étapes

### 1. Vérifier que tous les conteneurs tournent
`docker ps`
Tous les services concernés doivent être en statut « Up ». Sinon : `docker compose logs --tail 50` dans le dossier du service.

### 2. Vérifier les adresses dans les interfaces web
Entre conteneurs, on utilise le **nom du conteneur** (jamais `localhost`) et le **port interne** :

| Lien | Où le vérifier | Adresse attendue |
|---|---|---|
| Prowlarr → Radarr | Prowlarr, Settings, Apps | `http://radarr:7878` |
| Prowlarr → Sonarr | Prowlarr, Settings, Apps | `http://sonarr:8989` |
| Radarr / Sonarr → Prowlarr | Réglé automatiquement par la synchronisation | `http://prowlarr:9696` |
| Radarr / Sonarr → qBittorrent | Settings, Download Clients | hôte `qbittorrent`, port `8080` |

### 3. Vérifier les clés et identifiants
- La clé API de Radarr / Sonarr (Settings, General) doit être la même que celle saisie dans Prowlarr.
- Le nom d'utilisateur et le mot de passe de qBittorrent doivent être les mêmes que dans Radarr / Sonarr.

### 4. Tester chaque lien
Utiliser le bouton **Test** à côté de chaque connexion. Corriger le premier qui échoue, puis retester.

### 5. Vérifier les `docker-compose.yml`
- Les conteneurs concernés sont bien sur le **même réseau Docker** (même nom de réseau dans chaque fichier).
- Les noms de conteneurs (`container_name`) correspondent à ceux écrits dans les interfaces.
- Les dossiers `/media/downloads`, `/media/films` et `/media/series` sont montés de la même façon dans qBittorrent, Radarr et Sonarr.
- Après toute modification : `docker compose up -d`.

### 6. Vérifier les indexeurs
Dans Prowlarr, tester chaque indexeur. Un indexeur peut être temporairement en panne côté site : Prowlarr le désactive alors tout seul. Si seulement certains échouent, ce n'est pas un problème de configuration, il suffit d'attendre ou d'en ajouter un autre.

## Vérifier que ça a marché
- Tous les boutons Test sont verts.
- Une recherche manuelle dans Radarr ou Sonarr renvoie des résultats.
- Un téléchargement envoyé apparaît dans qBittorrent.

## Si ça ne marche pas
- Regarder les logs du service qui signale l'erreur : `docker logs <nom-du-conteneur> --tail 50`
- Ré-enregistrer la connexion dans l'interface (la supprimer puis la recréer).
- Redémarrer le service concerné : `docker compose restart`

## Historique (ce qui m'est arrivé)
Les deux fois, la cause était une mauvaise configuration entre les services. J'ai tout revérifié dans les interfaces web et dans les `docker-compose.yml` jusqu'à trouver l'erreur. *(À compléter : le paramètre exact qui était faux.)*
