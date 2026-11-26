# Décisions : sécurité

## Pourquoi UFW
- **Choix** : UFW comme pare-feu.
- **Alternative** : écrire directement les règles avec iptables ou nftables.
- **Pourquoi** : déjà intégré à Ubuntu, simple à installer, et suffisant pour mon usage.
- **Inconvénient** : moins précis que nftables. Docker contourne aussi UFW pour les ports qu'il publie lui-même, donc je ne publie que ceux du reverse proxy *(à vérifier avec `docker ps`)*.

## Pourquoi un reverse proxy avec HTTPS
- **Choix** : nginx comme point d'entrée unique, avec des certificats TLS.
- **Alternative** : publier directement les ports de chaque service.
- **Pourquoi** : un seul point d'entrée à protéger, trafic chiffré, et les conteneurs ne sont pas joignables directement.
- **Inconvénient** : si le reverse proxy tombe, tous les services deviennent inaccessibles.

## Pourquoi pas de port SSH ouvert, et Tailscale à la place
- **Choix** : aucun port SSH exposé sur Internet, avec Tailscale en accès de secours.
- **Alternative** : ouvrir SSH sur Internet.
- **Pourquoi** : je travaille sur le serveur en local, donc je n'ai pas besoin d'SSH depuis l'extérieur. Un port SSH ouvert est attaqué en permanence, alors que Tailscale n'expose rien.
- **Inconvénient** : si Tailscale ne fonctionne plus, je dois être en local pour administrer le serveur. Fail2ban est installé mais très peu utilisé.

## Pourquoi Wazuh, et le seuil de niveau 9 pour le bot
- **Choix** : Wazuh pour la supervision, et une alerte du bot dès le niveau 9.
- **Alternative** : pas de supervision, ou un seuil plus bas.
- **Pourquoi** : *(à compléter : pourquoi 9, par exemple pour éviter trop de bruit)*.
- **Inconvénient** : *(à compléter : par exemple le risque de rater des alertes de niveau inférieur)*.

## Compromis sur le téléphone (Vaultwarden)
- **Choix** : une politique de sécurité plus légère sur mon téléphone, pour ne plus retaper le master password à chaque déverrouillage.
- **Alternative** : demander le master password à chaque fois.
- **Pourquoi** : confort au quotidien, notamment après avoir oublié mon master password une fois.
- **Inconvénient** : si quelqu'un accède à mon téléphone déverrouillé, il peut accéder à mon coffre. *(À compléter : ce que j'ai exactement réglé, et ce qui limite ce risque.)*
