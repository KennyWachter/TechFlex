# Cahier des charges fonctionnel  
**Projet** : Mise en place d’un environnement de télétravail sécurisé hybride pour TechFlex  
**Auteurs** : Kenny Wachter; Othman Oumri 
**Date** : Juillet 2025  

---

## 1. Présentation du client fictif

**Nom de l’entreprise** : TechFlex  
**Secteur** : Conseil informatique  
**Taille** : PME d’environ 20 salariés  
**Contexte** :  
TechFlex souhaite moderniser son environnement de travail en proposant un accès sécurisé à ses outils et fichiers, aussi bien sur site qu’en télétravail. Le projet vise à combiner un **stockage local via NAS**, un accès distant via **VPN WireGuard**, et une **solution cloud professionnelle basée sur Microsoft 365**, le tout piloté via **Entra ID**.

---

## 2. Objectifs du projet

- Concevoir une **infrastructure hybride sécurisée** : locale + cloud Microsoft 365.
- Permettre aux utilisateurs d’accéder à leurs fichiers et outils de travail :
  - En local (réseau interne NAS TrueNAS)
  - À distance (via VPN WireGuard)
  - Depuis le cloud (OneDrive / SharePoint)
- Centraliser l’authentification avec **Entra ID** (anciennement Azure AD).
- Simuler l’architecture en environnement virtualisé (Proxmox) avant tout déploiement réel.
- Produire une documentation claire à destination des utilisateurs et de l’administration.

---

## 3. Périmètre du projet

### Inclus :
- Environnement virtualisé complet (Proxmox VE)
- Routeur virtuel avec pfSense + VPN WireGuard
- Poste de travail interne (LAN) et distant (via VPN)
- Serveur NAS TrueNAS SCALE (accès réseau local + synchronisation cloud)
- Suite Microsoft 365 (OneDrive, SharePoint, Teams, Outlook)
- Gestion des identités avec Entra ID
- Documentation complète (installation, utilisation, PRA/PCA, sécurité)

### Non inclus :
- Déploiement physique (NAS ou routeur réel)
- Gestion multi-sites ou multi-groupes
- Configuration avancée d’Exchange Online ou Intune

---

## 4. Besoins fonctionnels

| ID | Besoin | Description |
|----|--------|-------------|
| BF1 | Connexion VPN sécurisée | Accès distant au réseau local via WireGuard |
| BF2 | Stockage local centralisé | Accès aux fichiers via le NAS TrueNAS (SMB) |
| BF3 | Stockage et collaboration cloud | Accès à OneDrive, SharePoint, Teams, Outlook |
| BF4 | Gestion des identités | Comptes utilisateurs centralisés via Entra ID |
| BF5 | Synchronisation des données | NAS ↔ OneDrive (unidirectionnelle ou bidirectionnelle) |
| BF6 | Poste de travail complet | Accès simple et sécurisé depuis Windows 10/11 |

---

## 5. Besoins non fonctionnels

| ID   | Besoin                | Description |
|------|------------------------|-------------|
| BNF1 | Coût réduit            | Solutions gratuites ou comprises dans la licence M365 |
| BNF2 | Simplicité             | Interface utilisateur accessible à un public non technique |
| BNF3 | Modularité             | Possibilité d’ajouter des services (Intune, MFA, sauvegarde cloud) |
| BNF4 | Réalisme               | Environnement proche d’une PME réelle |

---

## 6. Livrables attendus

- Cahier des charges
- Justification des choix techniques
- Analyse des risques avec PRA / PCA
- Plan de conformité et de sécurité
- Documentation d’installation (VPN, Microsoft 365, accès NAS…)
- Documentation d’utilisation claire pour les employés
- Scripts d’automatisation (VPN, montage réseau, etc.)
- Support de présentation et plan de démonstration

---

## 7. Planning prévisionnel

| Semaine | Étape |
|---------|-------|
| 1 | Création des VM Proxmox et configuration réseau |
| 2 | Installation de pfSense + VPN WireGuard |
| 3 | Déploiement du NAS TrueNAS + partages |
| 4 | Intégration Microsoft 365 + Entra ID |
| 5 | Test des postes internes et distants |
| 6 | Documentation, tests utilisateurs, soutenance |

---
