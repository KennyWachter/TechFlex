# Analyse des risques + PRA / PCA  
**Projet : TechFlex – Télétravail Sécurisé Hybride**  
**Auteurs : Kenny Wachter, Othman Oumri**  
**Date : Juillet 2025**

---

## 1. Objectif du document

Ce document a pour but :

- D’identifier les risques techniques, humains et organisationnels pouvant compromettre la sécurité ou la disponibilité du système
- De proposer des mesures de prévention et de mitigation
- D’introduire un **Plan de Reprise d’Activité (PRA)** et un **Plan de Continuité d’Activité (PCA)** pour garantir la résilience de l’infrastructure

---

## 2. Analyse des risques

### 📌 2.1 Risques techniques

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Perte de connectivité VPN (WireGuard) | Élevée | Moyenne | Restart auto service + script de surveillance + double profil WireGuard en secours |
| Corruption du NAS (VM TrueNAS) | Élevée | Faible | Snapshots réguliers via Proxmox + export config TrueNAS |
| Interruption de la sync Google Drive | Moyenne | Moyenne | Surveillance des logs + réexécution manuelle + synchronisation locale en cache |
| Intrusion via DMZ (serveur web/mail) | Élevée | Moyenne | Règles strictes de pare-feu pfSense + VLAN/segmentation + logs + mises à jour |
| Défaillance de Proxmox (hyperviseur) | Élevée | Faible | Sauvegarde des VMs + export en OVA + doc de restauration |
| Manque d’espace sur le NAS | Moyenne | Moyenne | Alerte seuil disque + audit régulier des partages |

---

### 👤 2.2 Risques humains

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Mauvaise manipulation utilisateur (suppression fichier) | Moyenne | Élevée | Snapshots NAS + versioning activé sur Google Drive |
| Connexion sans VPN | Moyenne | Moyenne | Formation utilisateur + rappel affiché à l’ouverture de session |
| Utilisation de mot de passe faible | Élevée | Moyenne | Politique de mot de passe fort + tutoriel sécurité |
| Vol d’ordinateur portable personnel | Élevée | Faible | Utilisation de profils chiffrés + révocation rapide du profil VPN |

---

### 🏢 2.3 Risques organisationnels

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Non-respect du RGPD | Élevée | Faible | Aucune donnée sensible stockée sans consentement explicite, accès restreint, docs de conformité |
| Absence de sauvegardes régulières | Élevée | Moyenne | Plan de sauvegarde hebdomadaire Proxmox + TrueNAS (ZFS snapshots) |
| Mauvaise documentation | Moyenne | Moyenne | Wiki interne + doc partagée sur Drive + version imprimable |

---

## 3. Plan de Continuité d’Activité (PCA)

> Le PCA vise à **maintenir un niveau minimal de fonctionnement** pendant un incident technique ou organisationnel.

### 🔄 Mesures mises en œuvre :

| Incident potentiel | Solution de continuité | Délai maximal d’interruption |
|--------------------|------------------------|------------------------------|
| VPN inactif | Accès temporaire via solution de secours locale ou synchronisation en cache | 1 heure |
| Google Drive inaccessible | Travail temporaire en local sur NAS, synchronisation différée | 2 heures |
| NAS indisponible | Accès aux fichiers Google Drive (version cloud) | 1 heure |
| Proxmox en maintenance | Accès à la version cloud uniquement + synchronisation offline activée | 2 heures |

---

## 4. Plan de Reprise d’Activité (PRA)

> Le PRA décrit les **actions à effectuer pour rétablir un fonctionnement normal** après une interruption majeure.

### 🔁 Procédures prévues :

| Incident critique | Action immédiate | Délai de reprise cible | Responsable |
|-------------------|------------------|-------------------------|-------------|
| Corruption NAS (VM) | Restaurer snapshot + importer conf TrueNAS | < 2h | Admin |
| Compromission accès VPN | Révocation clé WireGuard + génération nouveau profil | < 1h | Admin |
| Perte VM Proxmox | Importer sauvegarde OVA + relancer services | < 3h | Admin |
| Données effacées par erreur | Restauration snapshot NAS ou Google Drive (versioning) | < 1h | Admin |

---

## 5. Outils de surveillance et d’alerting

| Élément | Outil utilisé | Type d’alerte |
|---------|---------------|----------------|
| Tunnel WireGuard | Script `ping` périodique + log systemd | Mail / log |
| Espace disque NAS | TrueNAS alertes internes | Web + mail |
| État VMs | Proxmox notifications + `pveproxy` logs | Journal local |
| Synchronisation GDrive | Logs rclone / apps | Affichage local / erreurs |
| Tentatives d’intrusion | pfSense logs + alertes fail2ban éventuelles | Journal + log exportable |

---

## 6. Conclusion

L’infrastructure TechFlex a été conçue avec une double logique :  
🔒 **Sécurité en priorité** (VPN, segmentation réseau, sauvegardes)  
⚙️ **Résilience et continuité** (cloud hybride, PRA/PCA, surveillance)

Ce plan assure un fonctionnement fiable, même en cas d’incident grave, et renforce la confiance des utilisateurs dans l’environnement de télétravail.

---
