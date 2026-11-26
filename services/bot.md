# Bot de supervision

## À quoi ça sert
Bot Python relié à Wazuh qui me prévient dès qu'une alerte de niveau 9 ou plus est détectée, et me permet de vérifier l'état de mon serveur à distance avec des commandes.

## Fonctionnalités
- **Alertes** : envoi d'un message dès qu'une alerte Wazuh atteint le niveau 9
- **Commandes** :
  - stockage disponible
  - utilisation de la RAM
  - température de la machine
  - état des conteneurs Docker

## Installation
- Lancé avec (à compléter : Docker, service systemd ou script lancé à la main)
- Plateforme de messagerie : (à compléter : Discord, Telegram...)
- Code source : (lien vers le dépôt)
- Comment il lit les alertes Wazuh : (à compléter : lecture du fichier d'alertes, API Wazuh, ou autre)

## Données et configuration
- Configuration et secrets dans un fichier `.env` (non publié dans le dépôt)
- Contenu : token du bot, identifiant de mon compte, accès à Wazuh

## Sécurité
- Exposé sur Internet : non, il initie seulement des connexions sortantes
- Le token est stocké hors du dépôt ; s'il fuit, je le régénère
- Seul mon compte est autorisé à utiliser les commandes (à compléter : confirmer que c'est bien vérifié dans le code)
- Les commandes sont en lecture seule : elles affichent des informations, elles ne modifient rien
- À améliorer : (à compléter)

## Problèmes rencontrés
- ...
