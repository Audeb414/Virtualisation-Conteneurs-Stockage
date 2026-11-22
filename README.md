# Virtualisation, conteneurs et stockage : travaux pratiques

Série de 5 travaux pratiques réalisés à l'Efrei Paris (module Virtualisation et Stockage, 2026), en binôme. Ce dépôt résume ce que j'ai mis en œuvre et appris à chaque TP. Les comptes rendus complets, avec captures d'écran, restent dans mes documents de cours.

> Il s'agit de TP de cours, réalisés en environnement de laboratoire (VMware Workstation Pro sous Windows 11).

## Vue d'ensemble

| TP | Thème | Ce que j'ai fait |
|---|---|---|
| 1 | Hyperviseur VMware ESXi | Installation d'ESXi 7.0 en environnement imbriqué, administration web, création et duplication de 2 VM Ubuntu, commutateur virtuel `vSwitch1` et réseau interne isolé |
| 2 | Gestion vSphere | Création et extension de banques de données VMFS, modèle de VM réutilisable, migrations P2V et V2V avec vCenter Converter Standalone |
| 3 | Docker | Installation depuis le dépôt officiel, cycle de vie des conteneurs, images personnalisées par `Dockerfile` (Apache, outils réseau, Firefox), nginx, publication sur Docker Hub, réseaux Docker |
| 4 | Docker Compose | Déploiement de 4 applications en stacks : WordPress + MySQL, GLPI + MariaDB, Nextcloud (dossiers locaux puis volumes Docker) et Home Assistant ; interface Portainer CE |
| 5 | Stockage en réseau | NAS avec NFS (export restreint, montage permanent dans `fstab`) et SAN avec iSCSI (cible `tgt`, client `iscsiadm`, authentification CHAP) |

## Compétences mises en œuvre

- **Virtualisation** : hyperviseur de type 1, VM imbriquées, commutateurs virtuels, banques de données VMFS, modèles, migrations P2V et V2V.
- **Conteneurs** : images et `Dockerfile`, réseaux utilisateur, `docker compose`, volumes, fichiers `.env` pour sortir les paramètres sensibles, diagnostic avec `docker logs`.
- **Stockage** : différences entre NAS (fichiers) et SAN (blocs), NFS, iSCSI, CHAP, montages persistants.
- **Dépannage documenté** : chaque compte rendu décrit les incidents rencontrés et leur résolution.

## Quelques problèmes résolus

- **Clavier et mot de passe root (ESXi)** : une disposition de clavier incohérente avec le clavier physique rendait la saisie impossible après redémarrage ; reprise en disposition cohérente.
- **Démarrage d'une VM** : un lecteur CD/DVD resté connecté à une ISO bloquait le démarrage.
- **Capacité insuffisante (P2V)** : l'assistant refusait la conversion car les disques sources dépassaient la banque de données ; vérification de l'espace libre en amont.
- **Image Firefox sous Docker** : échec sur l'image `ubuntu` (dépendance à `snap`), résolu avec `debian` et `firefox-esr`.
- **GLPI** : téléchargement échoué dans le conteneur, diagnostiqué avec `docker logs`.
- **NFS** : erreur « access denied by server » due à une adresse de client incorrecte dans `/etc/exports`.
- **iSCSI** : dossiers de configuration absents faute des paquets `tgt` et `open-iscsi`.

## Lien avec mes autres projets

Ces TP sont la base de mon projet [OSIRIS](https://github.com/Audeb414/OSIRIS-SIEM-Wazuh) (SIEM/XDR Wazuh conteneurisé sur Azure) et de la maquette de [MediConnect](https://github.com/Audeb414/MediConnect-Securisation-Reseau) (réseau sécurisé sous VirtualBox, Docker et pfSense).
