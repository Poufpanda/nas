# Page d'accueil (CV)

## À quoi ça sert
Vitrine statique qui me présente : mes projets, mes points Root-Me, mes liens HackTheBox et Credly et ce sur quoi je travaille.

## Installation
- Page en HTML/CSS pur, sans framework
- Servie par un conteneur `nginx:alpine` qui lit le dossier `/cv/src`
- Connecté au reverse proxy par un réseau Docker partagé
- Accessible via : https://mondomaine.duckdns.org

## Données et configuration
- Le contenu est dans `/cv/src`, modifié à la main (rien n'est dynamique)

## Sécurité
- Site statique : pas de base de données, pas de formulaire, donc très peu de surface d'attaque
- Exposé sur Internet : oui, en HTTPS

## Problèmes rencontrés
- Difficulte dans le developpement de la page a distance, mise en place d'un repo git ou je n'ai qu'a pull les dernieres versions de la page, et me permettant de travailler dessus de n'importe ou
