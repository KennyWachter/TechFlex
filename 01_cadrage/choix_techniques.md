# Justification des choix techniques (comparatifs)

Ce document explique, compare et justifie les technologies choisies dans le cadre du projet TechFlex – télétravail sécurisé hybride.

---

## 1. Choix de la plateforme de virtualisation : Proxmox VE

| Critère       | VirtualBox | VMware Workstation | **Proxmox VE** |
|---------------|------------|--------------------|----------------|
| Licence       | Gratuit    | Payant             | **Gratuit (open source)** |
| Performances  | Moyennes   | Très bonnes        | **Très bonnes** |
| Fonctionnalités pro | Faibles | Élevées           | **Élevées (clustering, snapshots, backup, accès web)** |
| Administration | Locale uniquement | Locale + Web | **Interface Web complète** |
| Support        | Communauté | Bon (payant)       | **Large communauté active** |

**Justification** : Proxmox est open source, stable, complet, et adapté aux environnements de test semi-pro. Il permet de créer plusieurs interfaces réseau pour simuler DMZ, LAN, Internet.

---

## 2. Choix du routeur/firewall : pfSense

| Critère         | **pfSense** | OPNsense | VyOS |
|------------------|------------|----------|------|
| Licence          | **Libre**  | Libre    | Libre |
| Interface Web    | **Oui**    | Oui      | Non (CLI uniquement) |
| Facilité de config | **Élevée** | Élevée  | Faible |
| VPN intégré      | **Oui (WireGuard/OpenVPN)** | Oui | Oui |
| Communauté       | **Très active** | Active | Plus technique |

**Justification** : pfSense est stable, bien documenté et adapté aux déploiements réels. Il permet de gérer le routage, les VLANs, les DMZ et le VPN WireGuard dans une seule interface.

---

## 3. Choix du VPN : WireGuard

| Critère         | **WireGuard** | OpenVPN | IPSec |
|------------------|---------------|---------|--------|
| Sécurité         | **Excellente** | Bonne   | Moyenne à bonne |
| Performance      | **Très élevée** | Moyenne | Moyenne |
| Configuration    | **Très simple** | Moyenne | Complexe |
| Compatibilité    | Très bonne     | Très bonne | Moyenne |
| Ressources       | **Faibles**    | Plus lourdes | Variables |
| **Licence / Coût** | **Gratuit (open source)** | Gratuit | Dépend des implémentations |

**Justification** : WireGuard est moderne, rapide, gratuit, open source, et très simple à déployer sur pfSense, Linux et Windows.

---

## 4. Choix du NAS : TrueNAS SCALE

| Critère           | TrueNAS CORE | **TrueNAS SCALE** | OpenMediaVault |
|--------------------|--------------|-------------------|----------------|
| Base OS            | FreeBSD      | **Debian Linux**  | Debian Linux   |
| Docker/Kubernetes  | Non          | **Oui**           | Oui (Docker uniquement) |
| Interface          | Très bonne   | **Très bonne**    | Moyenne |
| Plugins/Apps       | Nombreux     | **Modernes**      | Moins variés |
| Sync cloud         | Possible     | **Intégré via Apps** | Possible via plugin |
| **Licence / Coût** | **Gratuit (open source)** | **Gratuit (open source)** | Gratuit |

**Justification** : TrueNAS SCALE permet de créer des partages SMB classiques tout en utilisant des conteneurs pour synchroniser avec Google Drive. Il est open source, fiable, et orienté production.

---

## 5. Choix de l’outil cloud : Google Workspace

| Critère             | **Google Workspace** | Nextcloud | Microsoft 365 |
|----------------------|----------------------|-----------|----------------|
| Déploiement          | **Aucun (SaaS)**     | Auto-hébergement | SaaS |
| Outils intégrés      | **Drive, Docs, Gmail, Meet, Agenda…** | Fichiers uniquement | Office, Teams, Outlook |
| Intégration VPN/NAS  | **Oui, via rclone/Docker** | Oui (WebDAV) | OneDrive fermé |
| Accessibilité        | Navigateur | Navigateur ou client | Navigateur ou client |
| **Tarifs pro (€/utilisateur/mois)** | **Starter : 5,75 €**  \|  **Standard : 11,50 €**  \|  **Plus : 17,25 €** | Gratuit | **Basic : 5,60 €**  \|  **Standard : 11,70 €**  \|  **Premium : 22,60 €** |

**Justification** : Google Workspace offre une suite cloud complète (Drive, Docs, Gmail…) accessible via navigateur, sans installation locale. Sa haute disponibilité, son système de sécurité intégré et sa compatibilité avec les outils de synchronisation NAS (comme rclone ou Docker sur TrueNAS) en font une solution idéale pour une architecture hybride.
Elle est plus simple à déployer et à maintenir que Nextcloud (auto-hébergement) et plus flexible que Microsoft 365 sur la partie stockage.

---

## 6. Choix OS clients : Windows 10/11

| Critère            | **Windows** | Ubuntu Linux | macOS |
|--------------------|-------------|--------------|-------|
| Utilisation pro    | **Standard en entreprise** | Moyen | Faible |
| Accès SMB natif    | **Oui**     | Oui (via CIFS) | Oui |
| Client VPN         | **WireGuard officiel** | Oui | Oui |
| Intégration Google | **Totale** | Totale | Totale |

**Justification** : Windows est la norme dans la majorité des PME. L’accès SMB est natif, WireGuard fonctionne parfaitement, et les outils Google sont accessibles via navigateur.

---

## 📌 Résumé des choix retenus

| Composant         | Choix retenu          |
|-------------------|-----------------------|
| Hyperviseur       | Proxmox VE            |
| Routeur           | pfSense               |
| VPN               | WireGuard             |
| NAS               | TrueNAS SCALE         |
| Cloud             | Google Workspace      |
| Clients utilisateurs | Windows 10/11 Pro    |

---

