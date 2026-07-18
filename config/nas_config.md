# Configuration du Serveur NAS & Historique Matériel / NAS Server Configuration & Hardware History

Ce document détaille les spécifications techniques de la machine hôte faisant office de NAS, ainsi que les choix de l'OS et l'historique du montage matériel.
This document details the technical specifications of the host machine used as a NAS, and the choices of OS and modifications brought to it 

## Spécifications Matérielles / Hardware Specifications 

Le serveur est basé sur du matériel reconditionné
The server is based of refurbished hardware

* **Modèle d'origine :** HP omen 15
* **CPU :** Intel Core i5-7300HQ (4 Coeurs/4 Cores)
* **Carte Graphique / GPU :** NVIDIA GeForce GTX 1050 (2 ou 4 Go GDDR5 dédié/2 to 4 Go dedicated GDDR5)
* **Stockage / Storage :** 1To 5400T/min * *Note de Maintenance/Maintenance note :* Le disque dur d'origine étant défaillant, j'ai acheté un vieux pc portable d'occasion, et j'en ai retiré le disque dur pour le remplacer par le défaillant / Since the harddrive was failing, i've bought an old laptop, stripped the harddrive and mounted it my laptop
* **Refroidissement et Gestion / Cooling and Handling :** Serveur configuré pour pouvoir être géré sans écran, fermé, avec optimisations de la gestion d'alimentation pour un usage 24/7 / The server has been configured to be used screenless, with the lid closed, and with power optimisation for a 24/7 usage

## Système d'exploitation (OS) 

* **Distribution :** Ubuntu Server 24.04 LTS (Noble Numbat)
* **Architercture :** x86_64
* **Type d'installation / Installation mode :** Minimale/Headless (sans interface graphique, le moins de package installés, et connexion via OpenSSH / without user interface, as less packages as possible, and connection via OpenSSH)

## Stack Logicielle Initiale / Initial Software Stack 
L'ensemble des services est orchestré par **Docker** et **Docker-Compose** pour assurer une isolation et une maintenance simplifiée / Every service is orchestrated by **Docker** and **Docker-Compose** to ensure isolation and simplified maintenance :
* **Serveur Media / Media Server :** Jellyfin
* **Automatisation (Suite *Arr / *Arr Suite) :** Sonarr, Radarr, Prowlarr, Transmission/qBittorrent

---

## Journal de Bord / Résolution de Problèmes (Troubleshooting)
* **Symptôme / Problem :** Disque dur non reconnu par le BIOS et erreurs d'I/O lors des premiers boot / Harddrive was not recognized by the BIOS and I/O problems during the first boots
* **Résolution / Solution :**
*     1. Recherche de disque dur (SSD/HDD) / Searched for hard drive (SSD/HDD)
*     2. Recherche de pc, cassé ou pas sur des sites d'occasion pour en récupérer les pièces / Searched for a computer, broken or not on second hand websites to gather pieces
*     3. Remplacement du disque dur et confirmation de sa validité / Changed the hard drive and made sure it worked
 
