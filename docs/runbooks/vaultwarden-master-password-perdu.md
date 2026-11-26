# Master password Vaultwarden perdu : repartir depuis l'export .json

**Quand l'utiliser** : j'ai perdu le master password et je ne peux plus ouvrir mon coffre, mais j'ai un export `.json`.
**Pré-requis** : l'export `.json` (voir Attention ci-dessous) et accès à l'interface web de Vaultwarden.

## À savoir d'abord
- Le master password est **irrécupérable** : Vaultwarden ne le connaît pas, il sert à chiffrer le coffre. Restaurer une sauvegarde de `/data` ne le rend pas.
- On ne récupère donc pas l'ancien compte : on en crée un **nouveau** et on y **importe** les mots de passe.
- Si le `.json` est un export **non chiffré**, tout est lisible en clair par quiconque le trouve : le traiter comme un secret et le supprimer à la fin.
- Si le `.json` est un export **chiffré** : un export « protégé par mot de passe » s'importe avec le mot de passe de fichier choisi à l'export. Un export « restreint au compte » ne s'importe que dans l'ancien compte, donc inutilisable ici.

## Étapes
1. Vérifier que l'inscription est possible. Si elle est désactivée, l'autoriser temporairement
   (variable `SIGNUPS_ALLOWED=true` dans le `docker-compose.yml`, puis `docker compose up -d`).
2. Créer un nouveau compte sur `https://vaultwarden.<mon-domaine>` avec un **nouveau master password**.
3. Le noter immédiatement dans un endroit sûr hors de Vaultwarden.
4. Se connecter, puis : **Outils → Importer des données**.
5. Choisir le format **Bitwarden (json)**, sélectionner le fichier, lancer l'import.
6. Remettre l'inscription sur `SIGNUPS_ALLOWED=false` et relancer :
   `docker compose up -d`

## Vérifier que ça a marché
- Le nombre d'éléments du coffre correspond à celui de l'ancien (comparer avec le fichier).
- Tester 2 ou 3 connexions importantes, dont des comptes avec double authentification (les secrets TOTP sont dans l'export).
- Reconnecter l'extension navigateur et l'application téléphone au nouveau compte.

## Ce qui n'est PAS récupéré par l'export
- Les pièces jointes
- Les Send
- Les organisations et partages
- Les réglages du compte (par exemple la double authentification du compte Vaultwarden, à recréer)

## Nettoyage (important)
1. Supprimer l'export en clair : `shred -u export.json` (et les copies sur le PC ou le téléphone).
2. Faire une nouvelle sauvegarde propre de `/data` et un nouvel export chiffré, stockés ailleurs que sur le serveur.
3. Activer la double authentification sur le nouveau compte.

## Pour ne plus le reperdre
- Noter le master password sur papier, dans un endroit physique sûr, ou le confier à une personne de confiance.
- Tester une restauration de sauvegarde de temps en temps.
