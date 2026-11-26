# Parcours d'un média
 
Du moment où j'ajoute un film ou une série jusqu'à sa lecture dans Jellyfin.
 
```mermaid
sequenceDiagram
    autonumber
    actor U as Utilisateur
    participant S as Sonarr / Radarr
    participant P as Prowlarr
    participant I as Indexeurs
    participant Q as qBittorrent
    participant J as Jellyfin
 
    U->>S: Ajoute une série / un film
    S->>P: Demande une recherche de releases
    P->>I: Interroge les indexeurs configurés
    I-->>P: Renvoie les résultats
    P-->>S: Transmet les résultats
    S->>Q: Envoie le magnet / .torrent (avec une étiquette)
    Q->>Q: Télécharge dans /media/downloads
    loop Vérification régulière
        S->>Q: Le téléchargement est-il terminé ?
    end
    S->>S: Importe, renomme et range dans /media/films ou /media/series
    alt Connexion Jellyfin configurée dans Sonarr/Radarr
        S->>J: Demande l'actualisation de la bibliothèque
    else Sinon
        J->>J: Détecte le fichier au prochain scan
    end
    J-->>U: Média prêt à être visionné
```
 
Les indexeurs sont synchronisés une seule fois de Prowlarr vers Sonarr / Radarr, ce que ce schéma ne montre pas.
