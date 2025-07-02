# Justification des choix techniques (comparatifs)  
**Projet : TechFlex – Télétravail Sécurisé Hybride**  
**Auteur : Kenny Wachter**  
**Date : Juillet 2025**

---

## 1. Choix de la plateforme de virtualisation : Proxmox VE

| Critère       | VirtualBox | VMware Workstation | **Proxmox VE** |
|---------------|------------|--------------------|----------------|
| Licence       | Gratuit    | Payant             | **Gratuit (open source)** |
| Performances  | Moyennes   | Très bonnes        | **Très bonnes** |
| Fonctionnalités pro | Faibles | Élevées           | **Élevées (clustering, snapshots, backups)** |
| Interface admin | Locale    | Locale + UI        | **Web UI complète** |
| Support        | Communauté | Payant             | **Très actif (forums, docs)** |

**Justification** : Proxmox permet une virtualisation complète, un test de topologie réaliste et une gestion efficace via interface web. Il est open source, stable et utilisé en production dans de nombreuses PME.

---

## 2. Choix du VPN : WireGuard

| Critère         | **WireGuard** | OpenVPN | IPSec |
|------------------|---------------|---------|--------|
| Sécurité         | **Excellente (Curve25519)** | Bonne | Moyenne |
| Performance      | **Très élevée** | Moyenne | Moyenne |
| Configuration    | **Simple (1 fichier .conf)** | Moyenne (certificats) | Complexe |
| Compatibilité    | Tous OS       | Tous OS | Variable |
| Licence / Coût   | **Gratuit, open source** | Gratuit | Variable |

**Justification** : WireGuard est léger, rapide, ultra-sécurisé, très facile à configurer. Il s’intègre parfaitement avec pfSense et les postes Windows/macOS.

---

## 3. Choix du NAS : TrueNAS SCALE

| Critère             | TrueNAS CORE | **TrueNAS SCALE** | OpenMediaVault |
|----------------------|--------------|-------------------|----------------|
| OS de base           | FreeBSD      | **Debian Linux**  | Debian Linux   |
| Conteneurisation     | Non          | **Oui (Docker/K8s)** | Oui (Docker) |
| Interface web        | Très bonne   | **Très bonne**    | Moyenne |
| Gestion utilisateurs | Oui          | **Oui**           | Oui |
| Cloud Sync possible  | Limité       | **Oui (rclone, Nextcloud, OneDrive via App)** | Moyenne |
| Licence / Coût       | **Gratuit, open source** | **Gratuit** | Gratuit |

**Justification** : TrueNAS SCALE est stable, moderne, compatible Linux, intègre nativement des apps, et permet l’utilisation de scripts ou conteneurs pour la synchronisation OneDrive.

---

## 4. Choix de la suite collaborative : Microsoft 365

| Critère             | **Microsoft 365** | Google Workspace | Nextcloud |
|----------------------|------------------|------------------|------------|
| Collaboration        | **Teams, SharePoint, OneDrive, Outlook** | Gmail, Docs, Meet | Partage de fichiers |
| Intégration Windows  | **Totale (native)** | Bonne | Moyenne |
| Sécurité & conformité | **ISO, RGPD, MFA** | Bonne | À configurer |
| Authentification centralisée | **Oui (via Entra ID)** | Oui | Possible (LDAP) |
| Tarifs pro (€/utilisateur/mois) | **Basic : 5,60 €**, Standard : 11,70 €, Premium : 22,60 € | Starter : 5,75 € | Gratuit (mais à héberger) |

**Justification** : Microsoft 365 est une suite professionnelle complète, déjà utilisée en entreprise. Elle est parfaitement intégrée à Windows 10/11, centralise les données via OneDrive/SharePoint, et offre un écosystème unifié pour messagerie, réunions et collaboration.

---

## 5. Choix de la gestion des identités : Entra ID (anciennement Azure AD)

| Critère           | **Entra ID** | LDAP local | FreeIPA |
|--------------------|--------------|-------------|---------|
| Cloud natif        | **Oui**      | Non         | Non     |
| SSO / MFA          | **Oui (natif)** | Non         | Possible |
| Gestion M365       | **Intégrée** | Non         | Non     |
| Facilité d’usage   | **Interface web / auto provisionnement** | Complexe | Technique |
| Tarifs             | Inclus avec licences M365 | Gratuit | Gratuit |

**Justification** : Entra ID permet de centraliser les comptes utilisateurs M365 avec options de sécurité renforcées (MFA, audit, rôles). C’est la solution naturelle dans une architecture Microsoft.

---

## 6. Choix OS client : Windows 10/11

| Critère         | Windows 10/11 | Ubuntu | macOS |
|------------------|----------------|--------|--------|
| Compatibilité M365 | **Totale (native)** | Partielle | Très bonne |
| Client VPN WireGuard | **Oui (officiel)** | Oui | Oui |
| Accès NAS SMB     | **Natif**     | Oui    | Oui |
| Expérience utilisateur | **Standard PME** | Variable | Moins courant en PME |

**Justification** : Windows est utilisé dans la majorité des PME. Il offre un accès direct au NAS, un client VPN officiel, et une compatibilité native avec Microsoft 365.

---

## 📌 Résumé des choix retenus

| Composant               | Choix retenu         |
|-------------------------|----------------------|
| Hyperviseur             | Proxmox VE           |
| VPN                     | WireGuard            |
| NAS                     | TrueNAS SCALE        |
| Cloud collaboratif      | Microsoft 365        |
| Gestion des identités   | Entra ID (Azure AD)  |
| Postes clients          | Windows 10/11 Pro    |

---
