
# Sécurité

Le serveur est accessible depuis Internet, donc la surface d'exposition est réduite au strict nécessaire.

## Principes

- N'ouvrir que les ports dont j'ai réellement besoin.
- Un seul point d'entrée chiffré (reverse proxy en HTTPS).
- Ne pas exposer d'accès d'administration inutile.

## Mesures en place

### Adresse IP fixe
Mon fournisseur d'accès (Free) m'a permis de configurer une adresse IPv4 fixe, ce qui rend l'accès distant stable et prévisible.

### Pare-feu (UFW)
Tous les ports sans utilité sont fermés. Seuls les ports strictement nécessaires aux services publiés sont ouverts. *(À compléter : politique par défaut, liste des ports ouverts et justification de chacun, sans publier la configuration exacte si le dépôt est public.)*

### Reverse proxy et TLS (nginx)
Les services sont publiés derrière un reverse proxy nginx avec des certificats TLS, donc en HTTPS. Les conteneurs ne sont pas exposés directement.

### Fail2ban
Fail2ban est installé. Il est peu sollicité aujourd'hui car je n'ouvre pas de port SSH : j'administre le serveur en local.

### Accès distant d'administration (Tailscale)
Plutôt que d'ouvrir un port SSH sur Internet, j'ai configuré **Tailscale** (VPN maillé) comme accès de secours. Il permet d'atteindre le serveur depuis l'extérieur via un réseau privé chiffré, sans exposer de port supplémentaire.

### Supervision
Une instance Wazuh (installation minimale) est en place. *(À compléter : ce qui est surveillé et un exemple d'alerte traitée.)*

## Choix assumé : pas de SSH exposé

Je n'ai pas ouvert de port SSH car je ne m'en sers pas depuis l'extérieur. Cela supprime une des surfaces d'attaque les plus ciblées, au prix d'un accès à distance qui passe obligatoirement par Tailscale.

## Limites et améliorations prévues

- Documenter une procédure de sauvegarde et de restauration (notamment Vaultwarden, le service le plus sensible).
- Décrire la mise à jour régulière des images Docker et du système.
- Ajouter un modèle de menaces simple : ce que je protège, contre quoi, et par quels moyens.
- Isoler les conteneurs dans des réseaux Docker distincts si ce n'est pas encore le cas.
