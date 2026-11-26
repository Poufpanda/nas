# VaultWarden

## À quoi ça sert
VaultWarden garde des mots de passes et des logins de facon securise, permet l'autocompletion des mots de passes dans un formulaire, 
profite des applications de BitWarden mais reste OpenSource, possede un generateur de mot de passe securise

## Installation
- Lancé avec Docker (lien vers le docker-compose.yml)
- Connecté a nginx par un réseau Docker partagé : nginx le joint via le nom de conteneur 'vaultwarden'
- Accessible via : https://vaultwarden.mondomaine.duckdns.org

## Données et configuration
- Configuration : `/data`

## Sécurité
- Exposé sur Internet : oui, uniquement en HTTPS avec nginx
- Protections particulières : compte avec mot de passe fort, conteneur non joignable directement

## Problèmes rencontrés
- Oubli du Master Password a sa creation (mot de passe genere aleatoirement, impossible de le redeviner), nouveau compte + import du .json
- Installation d'une politique de securite plus legere sur mon telephone afin de ne plus avoir a mettre le master password a chaque deverouillage
