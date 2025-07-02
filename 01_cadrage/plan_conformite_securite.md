# Plan de conformité et de sécurité  
**Projet : TechFlex – Télétravail Sécurisé Hybride**  
**Auteurs** : Kenny Wachter; Othman Oumri  
**Date : Juillet 2025**

---

## 1. Objectif du document

Définir les mesures de sécurité mises en place dans l’architecture TechFlex et assurer une conformité minimale aux exigences d’une PME moderne, incluant la protection des données, l’accès distant, la confidentialité et la gouvernance des identités.

---

## 2. Sécurité des accès distants (VPN WireGuard)

| Élément            | Mesure appliquée |
|--------------------|------------------|
| Protocole          | WireGuard (chiffrement Curve25519, ChaCha20) |
| Authentification   | Clé publique/privée (pas de mot de passe) |
| Configuration client | Fichier `.conf` individuel fourni par l’administrateur |
| Journalisation     | Activée via logs systemd sur pfSense |
| Pare-feu           | Filtrage IP précis : seuls les postes autorisés accèdent au LAN |
| Révocation         | Suppression immédiate d’un profil en cas de vol/perte |

---

## 3. Sécurité des fichiers (NAS TrueNAS + OneDrive)

| Élément       | Mesure appliquée |
|---------------|------------------|
| NAS local     | Partages SMB/CIFS sécurisés avec authentification |
| Synchronisation cloud | OneDrive/SharePoint via conteneur ou rclone |
| Versioning    | Activé sur OneDrive et snapshots NAS |
| Accès distant | Uniquement via VPN sécurisé |
| Audit         | Journaux TrueNAS + logs OneDrive (Microsoft 365 Admin) |

---

## 4. Sécurité des comptes utilisateurs (Entra ID)

| Élément           | Mesure appliquée |
|-------------------|------------------|
| Annuaire central  | Entra ID (ancien Azure AD) |
| Authentification  | SSO Microsoft 365 + MFA obligatoire |
| Gestion des rôles | Attribution des droits par groupes de sécurité |
| Révocation rapide | En cas d’incident, blocage immédiat via console Entra |
| Journalisation    | Activité visible via audit logs et accès M365 Admin Center |

---

## 5. Sécurité des postes de travail

| Élément         | Mesure appliquée |
|-----------------|------------------|
| OS              | Windows 10/11 Pro (à jour) |
| Antivirus       | Windows Defender actif |
| Pare-feu        | Activé par défaut |
| Connexion VPN   | Requise avant accès aux fichiers locaux |
| Données locales | Minimales, stockage recommandé sur OneDrive |
| Sessions        | Verrouillage automatique au bout de 5 min |

---

## 6. Confidentialité en télétravail

| Risque potentiel | Mesure appliquée |
|------------------|------------------|
| Environnement non sécurisé (lieu public) | Sensibilisation à l’isolement visuel et sonore (écran non visible par des tiers, port du casque) |
| Réutilisation de PC personnel | Préférence pour des postes fournis ou comptes limités à usage pro |
| Écoute passive | Formation utilisateur + recommandation de lieux calmes |

---

## 7. Conformité RGPD (dans le cadre d’un déploiement réel)

| Principe RGPD               | Application dans ce projet |
|-----------------------------|-----------------------------|
| Minimisation des données    | Aucune donnée sensible traitée sans consentement |
| Droit d’accès / suppression | Géré via OneDrive / Entra ID |
| Journalisation              | Activée (NAS + M365 + VPN) |
| Stockage                   | Données stockées dans OneDrive + NAS sécurisé |
| Sécurité contractuelle      | Si M365 en prod réelle : clauses RGPD Microsoft fournies |

---

## 8. Contrôle périodique du système

| Élément contrôlé | Fréquence | Responsable |
|------------------|-----------|-------------|
| Audit comptes utilisateurs (Entra ID) | **Trimestriel** | Admin Microsoft 365 |
| Vérification des accès VPN | **Trimestriel** | Admin réseau |
| Contrôle du quota/disque (NAS) | **Trimestriel** | Admin stockage |
| Tests PRA (VM / sync) | **Trimestriel** | Admin général |
| Mise à jour des logiciels (NAS, pfSense, VMs) | À chaque patch critique ou contrôle programmé | Admin |

📌 **But** : éviter les dérives, les accès obsolètes ou les failles dormantes dans le système.

---

## 9. Principes appliqués

- 🔐 **Principe du moindre privilège**
- 🧩 **Séparation des zones réseau** (DMZ, LAN, VPN)
- 🔁 **Double sauvegarde** (OneDrive versioning + NAS snapshot)
- 🔍 **Traçabilité des accès** (audit, journalisation)
- 💡 **Formation utilisateurs** (sécurité, télétravail, outils)

---

## 10. Conclusion

L’infrastructure TechFlex intègre dès la conception :
- Des outils reconnus et sécurisés (WireGuard, Entra ID, Microsoft 365)
- Un contrôle des accès rigoureux
- Un audit trimestriel systématique pour renforcer la posture sécurité
- Une adaptation à la réalité d’une PME hybride (local + cloud + télétravail)

---
