# Cahier des charges fonctionnel  
**Projet** : Mise en place d’un environnement de télétravail sécurisé hybride pour TechFlex  
**Auteurs** : Kenny Wachter; Othman Oumri  
**Date** : Juillet 2025  

---

## 1. Présentation du client

**Nom de l’entreprise** : TechFlex  
**Secteur** : Conseil informatique  
**Taille** : PME d’environ 20 salariés  
**Contexte** :  
TechFlex souhaite moderniser son environnement de travail et permettre à ses collaborateurs d’accéder à leurs outils et fichiers à la fois en local et à distance, de manière sécurisée.

---

## 2. Objectifs du projet 
####*Pour démonstration au client avant de le mettre en production*
- Créer une infrastructure réseau virtualisée avec Proxmox VE.
- Mettre en place un NAS local (TrueNAS SCALE) accessible :
  - en local via le réseau LAN
  - à distance via VPN (WireGuard)
- Synchroniser les fichiers entre le NAS et Google Workspace (Drive).
- Simuler une DMZ avec des services accessibles de l’extérieur (web/mail).
- Tester les accès et la synchronisation depuis deux postes : interne et externe.
- Documenter toute l’infrastructure pour futur déploiement physique.

---

## 3. Périmètre du projet

### Inclus :
- Virtualisation complète (Proxmox VE)
- Réseaux Internet, LAN, DMZ, Extérieur simulés
- Routeur virtuel avec pfSense + WireGuard
- NAS TrueNAS SCALE
- Serveurs web/mail en DMZ
- 2 postes clients (interne & externe)
- Synchronisation NAS ↔️ Google Drive
- Documentation complète

### Non inclus :
- Déploiement réel sur infrastructure physique
- SSO/LDAP
- Multi-sites

---

## 4. Besoins fonctionnels

| ID  | Besoin                           | Description |
|-----|----------------------------------|-------------|
| BF1 | Accès sécurisé au réseau interne | VPN WireGuard |
| BF2 | Stockage local                   | NAS TrueNAS (SMB) |
| BF3 | Accès cloud synchrone            | Sync Google Drive |
| BF4 | Services publics DMZ             | Web / Mail |
| BF5 | Accès utilisateur                | Poste interne + externe |
| BF6 | Environnement réaliste           | Simulation avant production |

---

## 5. Besoins non fonctionnels

| ID    | Besoin             | Description |
|-------|--------------------|-------------|
| BNF1  | Coût nul           | Logiciels open source/gratuits |
| BNF2  | Maintenance simple | Documentation claire |
| BNF3  | Modularité         | Extension possible |
| BNF4  | Réalisme           | Architecture type entreprise |

---

## 6. Livrables attendus

- Infrastructure virtualisée fonctionnelle
- Documentation technique
- Cahier des charges
- Analyse des risques (avec PRA/PCA)
- Comparatif technique
- Rapports de surveillance + scripts
- Support de soutenance

---

## 7. Planning prévisionnel

| Jour | Étape                                 |
|---------|----------------------------------------|
| 1       | Mise en place de Proxmox + topologie  |
| 2       | Installation pfSense + WireGuard      |
| 3       | Déploiement NAS + Google Sync         |
| 4       | Postes internes et externes           |
| 5       | Tests + documentation                 |
| 6       | Finalisation livrables + soutenance   |

---
