# Plan de conformité et de sécurité  
**Projet : TechFlex – Télétravail Sécurisé Hybride**  
**Auteurs : Kenny Wachter, Othman Oumri**  
**Date : Juillet 2025**

---

## 1. Objectif du document

Ce document présente les mesures de sécurité mises en place dans l’architecture TechFlex ainsi que les dispositions de conformité, notamment vis-à-vis des principes du RGPD, de la protection des données, de l’accès distant sécurisé et de la confidentialité des échanges.

---

## 2. Sécurité des accès distants (VPN)

| Élément            | Mesures appliquées |
|--------------------|--------------------|
| Protocole VPN      | WireGuard, chiffrement Curve25519 |
| Authentification   | Par clé publique/privée |
| Révocation d’accès | Suppression de la clé publique dans la conf serveur |
| Sécurité client    | Profil .conf distribué manuellement |
| Journalisation     | Logs systemd activés sur pfSense |
| Tunnels isolés     | Règles de pare-feu filtrant l’accès aux seules ressources autorisées |

---

## 3. Sécurité des fichiers et du NAS

| Élément          | Mesures appliquées |
|------------------|--------------------|
| Partages         | NAS via SMB/CIFS, accès contrôlé |
| Contrôle d’accès | Par utilisateurs/groupes TrueNAS |
| Chiffrement      | ZFS (optionnel), accès uniquement via VPN |
| Disponibilité    | Snapshots + sauvegardes Proxmox |
| Sauvegarde       | Export VM et configuration |
| Audit            | Journaux d’accès activés sur TrueNAS |

---

## 4. Sécurité du cloud (Google Workspace)

| Élément           | Mesures appliquées |
|-------------------|--------------------|
| Compte Google     | Compte dédié au projet |
| Authentification  | Double facteur possible en usage réel |
| Intégration NAS   | Sync via rclone ou Apps Docker |
| Confidentialité   | Pas de données personnelles sensibles stockées |
| Versioning        | Activé sur Google Drive |

---

## 5. Conformité RGPD

| Principe RGPD               | Application dans le projet |
|-----------------------------|-----------------------------|
| Minimisation des données    | Aucune donnée personnelle sensible utilisée |
| Droit d’accès/suppression   | Les fichiers sont sous contrôle de l’entreprise |
| Traçabilité                 | Journalisation NAS + VPN |
| Consentement                | Simulé, mais appliqué en pratique |
| Localisation des données    | NAS local + Google Drive (cloud) |

---

## 6. Sécurité des postes clients

| Élément         | Mesures appliquées |
|-----------------|--------------------|
| OS              | Windows 10/11 Pro |
| Antivirus       | Windows Defender |
| Pare-feu        | Activé sur chaque poste |
| Mises à jour    | Automatiques simulées |
| Accès NAS       | Lecteur réseau mappé, via VPN |
| Stockage local  | Limité, usage du cloud privilégié |

---

## 7. Politique de mot de passe

| Élément         | Politique appliquée |
|-----------------|----------------------|
| Longueur        | ≥ 10 caractères |
| Complexité      | Majuscule + chiffre + caractère spécial |
| Renouvellement  | Recommandé (non imposé dans ce test) |
| Transmission    | Pas de mot de passe envoyé par mail |
| Stockage        | Aucun mot de passe stocké en clair |

---

## 8. Règles pare-feu et segmentation réseau

| Zone            | Règles principales |
|------------------|-------------------|
| WAN ↔ pfSense     | Ports nécessaires uniquement (UDP 51820) |
| pfSense ↔ LAN     | Accès NAS et poste interne autorisé |
| pfSense ↔ DMZ     | Ports HTTP/HTTPS ouverts uniquement |
| DMZ ↔ LAN         | Isolation stricte (bloqué) |
| VPN ↔ LAN         | Accès contrôlé aux IP internes |
| VPN ↔ DMZ         | Interdit |

---

## 9. Principes appliqués

- 🔐 **Principe du moindre privilège**
- 🔁 **Séparation réseau (DMZ, LAN, VPN, WAN)**
- 🔍 **Journalisation des accès**
- 💡 **Sensibilisation utilisateur simulée**
- 📁 **Centralisation des fic**
