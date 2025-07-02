# Documentation d'installation – TechFlex  
**Public cible : Employés et employeurs (non-informaticiens)**  
**Dernière mise à jour : Juillet 2025**

---

## Objectif du document

Ce guide présente les éléments que les utilisateurs doivent installer eux-mêmes sur leur poste de travail (fixe ou portable), que ce soit en interne ou à distance.

Les installations système, réseau et serveurs (comme TrueNAS, pfSense, etc.) sont déjà prises en charge par le service informatique et ne sont **pas à refaire par les utilisateurs**.

---

## 1. Installation du client VPN WireGuard

### 📌 À quoi ça sert ?  
Permet de se connecter à distance au réseau de l'entreprise de façon sécurisée.

### 📥 Télécharger WireGuard

- Site officiel : [https://www.wireguard.com/install](https://www.wireguard.com/install)
- Choisir la version correspondant à votre système :
  - Windows 10 ou 11 → *WireGuard for Windows*
  - macOS → *WireGuard for macOS*
  - Android → Disponible sur Google Play
  - iOS → Disponible sur App Store

### 🧭 Étapes (Windows)

1. Télécharger le fichier d’installation.
2. Lancer l’installation en double-cliquant sur le fichier.
3. Une fois installé, ouvrir l'application WireGuard.
4. Cliquer sur **"Importer un tunnel depuis un fichier"**.
5. Sélectionner le fichier `.conf` qui vous a été fourni par l'administrateur (ex : `techflex-vpn.conf`).
6. Cliquer sur **"Activer"**.

✅ Le VPN est maintenant prêt. Il s’activera à la demande ou automatiquement selon la configuration.

---

## 2. Accès à l’emplacement réseau (NAS)

### 📌 À quoi ça sert ?  
Accéder à un dossier partagé de l’entreprise contenant vos documents de travail.

### 🖥️ Systèmes compatibles : Windows uniquement

### 🧭 Étapes (Windows)

1. Ouvrir l’explorateur de fichiers.
2. Cliquer sur **"Ce PC"**, puis sur **"Connecter un lecteur réseau"**.
3. Choisir une lettre de lecteur (par exemple `Z:`).
4. Dans le champ **Dossier**, saisir l'adresse réseau qui vous a été fournie (ex : `\\nas.techflex.lan\partage`).
   - Si vous êtes à distance : vous devez d’abord activer le VPN.
5. Cochez **"Se reconnecter à l’ouverture de session"**.
6. Si demandé, entrez le **nom d’utilisateur et mot de passe** fournis.

✅ Le lecteur réseau apparaîtra ensuite automatiquement dans "Ce PC".

---

## 3. Installation de Google Drive (optionnel mais recommandé)

### 📌 À quoi ça sert ?  
Accéder à vos fichiers Drive hors connexion et assurer une synchronisation automatique locale ↔ cloud.

### 📥 Télécharger Google Drive pour ordinateur

- Lien officiel : [https://www.google.com/intl/fr/drive/download](https://www.google.com/intl/fr/drive/download)

### 🧭 Étapes (Windows)

1. Télécharger le fichier d’installation.
2. Lancer l’installation.
3. Se connecter avec votre compte Google (utilisé pour le travail).
4. Choisir les dossiers que vous souhaitez synchroniser.
5. Activer l’option **"Accès hors connexion"** si vous souhaitez pouvoir travailler sans Internet.

✅ Un dossier **"Google Drive"** sera créé sur votre poste.

---

## 4. Outils facultatifs (navigateur, suite bureautique)

> Ces outils ne sont pas obligatoires mais recommandés pour un usage confortable.

| Outil | Utilité | Téléchargement |
|-------|---------|----------------|
| **Google Chrome** | Meilleure compatibilité avec Google Workspace | [https://www.google.com/chrome/](https://www.google.com/chrome/) |
| **LibreOffice** | Édition hors ligne de documents si vous n'avez pas Microsoft Office | [https://fr.libreoffice.org/](https://fr.libreoffice.org/) |

---

## 5. Assistance et support

En cas de difficulté, contactez le service informatique de TechFlex ou suivez le guide d'utilisation prévu pour chaque outil (à venir dans la documentation d'utilisation).

---

## ✅ Résumé

| Élément à installer | Obligatoire | Public concerné |
|---------------------|-------------|------------------|
| WireGuard VPN       | ✅ Oui       | Télétravailleurs |
| Lecteur réseau SMB  | ✅ Oui       | Tous             |
| Google Drive        | ⬜ Recommandé | Tous             |
| Navigateur Chrome   | ⬜ Optionnel  | Tous             |

---

