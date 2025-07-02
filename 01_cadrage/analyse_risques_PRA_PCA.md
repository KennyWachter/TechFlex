# Analyse des risques + PRA / PCA  
**Projet : TechFlex – Télétravail Sécurisé Hybride**  
**Auteurs** : Kenny Wachter; Othman Oumri 
**Date : Juillet 2025**

---

## 1. Objectif du document

Ce document vise à :

- Identifier les principaux risques de sécurité, de confidentialité et de disponibilité
- Mettre en place des mesures de prévention ou de correction
- Définir un **Plan de Reprise d’Activité (PRA)** et un **Plan de Continuité d’Activité (PCA)** pour assurer la résilience de l’environnement Microsoft 365 + NAS + VPN

---

## 2. Analyse des risques

### 📌 2.1 Risques techniques

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Perte de connectivité VPN | Élevée | Moyenne | Redémarrage auto du service WireGuard + documentation utilisateur claire |
| Interruption synchronisation OneDrive ↔ NAS | Moyenne | Moyenne | Journaux de synchronisation surveillés + relance manuelle via conteneur |
| Panne du NAS | Élevée | Faible | Snapshots Proxmox + sauvegarde config NAS externe |
| Erreur de config pare-feu pfSense | Élevée | Faible | Export régulier de la conf + test de restauration |
| Défaillance Proxmox | Élevée | Faible | Export OVA hebdo + restauration sur autre hôte |
| Saturation espace disque NAS | Moyenne | Moyenne | Alertes de capacité + quota utilisateur |

---

### 👤 2.2 Risques humains

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Suppression accidentelle de fichiers | Moyenne | Élevée | Versioning OneDrive + snapshots NAS |
| Utilisation de mot de passe faible | Élevée | Moyenne | Entra ID : politique de mot de passe + MFA |
| Connexion sans VPN | Moyenne | Moyenne | Notification + tuto d'accès obligatoire via WireGuard |
| Confidentialité non respectée en télétravail | Moyenne | Moyenne | Formation à l’**isolement visuel et auditif** (ne pas travailler à voix haute en public, écran visible uniquement par l’utilisateur, port du casque) |
| Vol d’un PC portable | Élevée | Faible | Session verrouillée + chiffrement disque + révocation du compte Entra ID |

---

### 🏢 2.3 Risques organisationnels

| Risque | Gravité | Probabilité | Mesures |
|--------|---------|-------------|---------|
| Absence de sauvegardes régulières | Élevée | Moyenne | Snapshot VMs + backup NAS externe planifié |
| Mauvais encadrement utilisateur | Moyenne | Moyenne | Guide utilisateur simple + wiki partagé SharePoint |
| Mauvaise gestion des accès | Élevée | Moyenne | Attribution de rôles via Entra ID + logs d’activité |
| Non-respect RGPD | Moyenne | Faible | Aucun stockage de données sensibles dans le cadre de ce projet pédagogique |

---

## 3. Plan de Continuité d’Activité (PCA)

> Maintenir un fonctionnement partiel pendant l'incident

| Incident potentiel | Solution temporaire | Délai d’interruption max |
|--------------------|---------------------|---------------------------|
| NAS indisponible   | Travail via OneDrive uniquement | 2 heures |
| Connexion VPN impossible | Travail hors ligne sur fichiers déjà synchronisés | 1 heure |
| Sync NAS ↔ cloud interrompue | Synchronisation différée manuelle | 1 jour |
| Poste de travail HS | Connexion depuis un autre poste via M365 (web) | 30 min |

---

## 4. Plan de Reprise d’Activité (PRA)

> Rétablir l’activité complète après un incident critique

| Incident | Action de reprise | Délai cible | Responsable |
|----------|-------------------|-------------|-------------|
| Corruption de la VM NAS | Restauration snapshot Proxmox + config NAS | 2h | Administrateur |
| Compromission compte VPN | Révocation profil WireGuard + génération nouveau | 30 min | Admin réseau |
| Perte de VM pfSense | Restauration OVA + import conf pare-feu | 1h | Admin réseau |
| Compte Microsoft compromis | Réinitialisation Entra ID + audit OneDrive | 1h | Admin Microsoft 365 |
| Effacement massif OneDrive | Restauration via corbeille ou versioning | 30 min | Utilisateur + admin |

---

## 5. Outils de supervision & alerting

| Élément | Outil utilisé | Type d’alerte |
|---------|---------------|----------------|
| VPN WireGuard | Logs journal + test script connectivité | Journal local |
| NAS (disques) | Alertes SMART + quota utilisateur TrueNAS | Mail / interface |
| Espace disque VM | Interface Proxmox + script bash | Notification locale |
| Sync cloud | Logs conteneur ou rclone (journal, webhook) | Fichier / console |
| Activité utilisateur | Audit Entra ID / OneDrive | Via Microsoft 365 |

---

## 6. Conclusion

L’environnement TechFlex est conçu pour combiner :
- 🔐 **Sécurité renforcée** : VPN, MFA, segmentation, droits contrôlés
- 🧠 **Simplicité d’usage** : outils connus (Windows, Microsoft 365)
- 🔁 **Résilience** : sauvegardes, PRA/PCA, accès cloud
- 📚 **Sensibilisation utilisateur** : documentation + formation confidentialité en télétravail

Le tout dans un cadre réaliste de PME, avec des outils modernes, stables et maintenables.

---
