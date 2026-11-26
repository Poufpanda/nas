# Configurations

Ce dossier contient les fichiers de configuration de mon serveur, **nettoyés de tout secret**, pour pouvoir reconstruire l'installation.

## Contenu

```
configs/
├── README-configs.md                    (ce fichier)
├── .env.example                 (variables attendues, sans valeurs réelles)
├── ufw.md                       (règles du pare-feu)
├── npm-proxy-hosts.md           (table des hôtes du reverse proxy)
└── compose/
    ├── jellyfin-radarr-sonarr-prowlarr-qbittorrent-nginx/docker-compose.yml
    ├── vaultwarden/docker-compose.yml
    └── homepage/docker-compose.yml
```

Chaque `docker-compose.yml` se lance avec `docker compose up -d` depuis son dossier.

## Avant de lancer les services : le réseau partagé

Tous les services rejoignent le même réseau Docker que le reverse proxy, créé une seule fois :

```bash
docker network create proxy
```

Ce réseau permet à nginx de joindre chaque service par son nom de conteneur, sans publier les ports sur la machine.

## Ce qui n'est jamais publié

- Mots de passe, tokens, clés API (Radarr, Sonarr, Prowlarr), `ADMIN_TOKEN` de Vaultwarden
- Le vrai nom de domaine et l'adresse IP publique
- Les dossiers `config/` et `data/` des services (bases de données, clés, sauvegardes de Vaultwarden)
- Les certificats et clés privées (`letsencrypt/`)

Les valeurs sensibles vont dans un fichier `.env` (voir `.env.example`), listé dans `.gitignore`.

## Versions

Les fichiers utilisent `latest` : j'ai le réflexe de prendre la dernière version. Le défaut est qu'une mise à jour peut casser un service sans que je sache de quelle version je venais. Avant une mise à jour, je note donc la version en cours (voir le runbook de mise à jour) pour pouvoir revenir en arrière. Pour un service critique comme Vaultwarden, je peux fixer un numéro de version.

## Avant de publier le dépôt

1. Chercher les fuites : `grep -rniE "password|token|apikey|secret" .`
2. Valider chaque fichier : `docker compose config` (affiche la configuration finale ou une erreur).
3. Vérifier que `.env` n'est pas suivi par Git : `git status`.
4. Option : installer `gitleaks` pour bloquer les commits contenant un secret.
