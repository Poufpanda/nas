# Décisions : matériel et système

## Pourquoi ce PC (HP Omen 15)
- **Choix** : un ancien PC portable HP Omen 15 (2015) que je n'utilisais plus.
- **Alternative** : un serveur neuf, ou un autre de mes anciens PC.
- **Pourquoi** : c'était la machine avec les meilleures caractéristiques parmi celles que je possédais, et elle a une carte graphique externe au CPU qui peut aider Jellyfin pour le transcodage vidéo. Cela ne m'a rien coûté.
- **Inconvénient** : matériel ancien, consommation plus élevée qu'un petit serveur dédié.

## Pourquoi un disque dur d'occasion
- **Choix** : un HDD de 1 To d'occasion, récupéré dans un PC portable fonctionnel.
- **Alternative** : un disque neuf.
- **Pourquoi** : les disques de mes anciens PC étaient tous défaillants, et les disques neufs étaient trop chers pour ce projet.
- **Inconvénient** : fiabilité incertaine, et un seul disque est un point de défaillance unique. Une sauvegarde externe est prévue.

## Pourquoi Ubuntu Server
- **Choix** : Ubuntu Server.
- **Alternative** : une autre distribution Linux.
- **Pourquoi** : c'est la distribution que je pense être la plus simple pour un premier serveur auto-hébergé.
- **Inconvénient** : *(à compléter si j'en vois un)*.

## Pourquoi Docker
- **Choix** : un conteneur Docker par service.
- **Alternative** : installer chaque logiciel directement sur le système.
- **Pourquoi** : chaque service est isolé des autres, simple à déployer avec un `docker-compose.yml`, et facile à mettre à jour ou à réinstaller.
- **Inconvénient** : une couche de plus à comprendre, et Docker modifie lui-même les règles de pare-feu (voir [securite.md](securite.md)).
