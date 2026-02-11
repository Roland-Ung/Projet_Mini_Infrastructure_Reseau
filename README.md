# Conception et déploiement d'une infrastructure réseau pédagogique

⚠️ Ce projet est personnel et ne remplace pas une vrai infrastructure réseau

## Objectifs
Configurer et sécuriser une architecture complète incluant :
- Active Directory
- DNS
- DHCP
- Serveur de fichiers
- Gestion des permissions NTFS avancées
- GPO
- Pare-feu Debian avec NAT (nftables)
- Sauvegarde système

## Environnement
- Client : Windows 2000 pro
- Contrôleur de domaine : Windows Server 2016
- Serveur de fichiers : Windows Server 2016
- Pare-feu : Linux Debian

## Technologies utilisés
- VMware Workstation
- Windows Server 2016
- Windows 2000 Professionnel
- Debian Linux
- nftables
- NTFS Permissions
- Group Policy Management

## Fonctionnalités

### 1 - Sécurisation du réseau
Mise en place d'un pare-feu sous `nftables` avec :
- Configuration du NAT pour l'accès Internet des clients.
- Filtrage restrictif des flux entrants/sortants.
- Protection contre le spoofing et isolation du LAN

### 2 - Gestion centralisée (Active Directory)
- Création d'une structure d'Unités d'Organisation (OU_Professeurs, OU_Etudiants).
- Déploiement de **GPO** : blocage du panneau de configuration et restriction d'installation.
- Automatisation de l'adressage via un serveur DHCP Windows.

### 3. Gestion Avancée du Stockage (ACL NTFS)
Configuration de partages réseau avec gestion fine des droits :
- **Espace Cours :** Lecture seule pour les étudiants, contrôle total pour les enseignants.
- **Espace Copies :** Ecriture seule pour les étudiants sans droit de lecture sur le dossier.

### 4. Plan de Continuité (Sauvegarde)
- Configuration de **Windows Server Backup** sur un disque dédié.
- Sauvegarde quotidienne planifiée de l'**Active Directory** et des données critiques.

## Clôner le dépôt
```bash
git clone https://github.com/Roland-Ung/Projet_Mini_Infrastructure_Reseau.git
```

## Structure du projet
```
Projet_Mini_Infrastructure_Reseau/
│
├── scripts/
│   └── nftables.conf               # Script de pare-feu
├── architecture_réseau/
│   ├── plan_adressage.csv          # Détails sur l'IP, rôle, mode VMware de chaque machine
│   └── diagramme_réseau.png        # Modélisation de l'infrastructure réseau
├── documentation_projet.pdf        # Etapes des installations et configurations
└── README.md               
```
