# Pare-feu UFW

Politique : tout ce qui entre est refusé par défaut, seuls les ports nécessaires sont ouverts.

## Règles

```bash
# Politique par défaut
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Reverse proxy (HTTP pour la redirection et les certificats, HTTPS pour les services)
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Serveur Minecraft (seulement si ouvert aux autres joueurs)
# sudo ufw allow 25565/tcp

# Activer
sudo ufw enable
```

Aucun port SSH n'est ouvert : j'administre le serveur en local, avec Tailscale en accès de secours.

## Vérifier

```bash
sudo ufw status verbose
```

## À savoir

Docker écrit lui-même ses règles de pare-feu pour les ports qu'il publie, et ces règles contournent UFW. UFW ne suffit donc pas : je ne publie que les ports du reverse proxy et je vérifie avec :

```bash
docker ps --format "table {{.Names}}\t{{.Ports}}"
sudo ss -tulpn
```
