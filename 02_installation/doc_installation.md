# Documentation d'installation – TechFlex  
**Public : Employés / Employeurs (non informaticiens)**  
**Dernière mise à jour : Juillet 2025**

---

## 🎯 Objectif

Ce guide explique comment installer et configurer les outils essentiels pour accéder aux fichiers et services de l'entreprise TechFlex :

- VPN sécurisé (WireGuard)
- Microsoft 365 (OneDrive, Outlook, Teams…)
- Accès au dossier partagé de l’entreprise (NAS)

---

## 1. Installation du client VPN WireGuard

### 🧩 Pourquoi ?
Le VPN vous permet d'accéder de manière sécurisée aux fichiers et ressources de l'entreprise à distance (depuis chez vous ou en déplacement).

### 📥 Télécharger WireGuard
- Windows : [https://www.wireguard.com/install](https://www.wireguard.com/install)
- macOS : Disponible sur App Store
- Android : Google Play – "WireGuard"
- iOS : App Store – "WireGuard"

### 🧭 Étapes (Windows) :

1. Télécharger l’installateur depuis le lien ci-dessus.
2. Lancer l'installation.
3. Ouvrir WireGuard.
4. Cliquer sur **"Importer un tunnel depuis un fichier"**.
5. Sélectionner le fichier `techflex-vpn.conf` fourni par l’entreprise.
6. Cliquer sur **"Activer"**.

✅ Une fois activé, vous êtes connecté au réseau sécurisé de TechFlex.

---

## 2. Connexion au dossier partagé (lecteur réseau NAS)

### 🧩 Pourquoi ?
Cela vous permet d'accéder aux fichiers partagés de l’entreprise, stockés localement sur le NAS.

### 🧭 Étapes (Windows uniquement) :

1. Ouvrir **"Ce PC"** dans l'explorateur de fichiers.
2. Cliquer sur **"Connecter un lecteur réseau"**.
3. Choisir une lettre (ex : `Z:`).
4. Dans le champ **Dossier**, entrer l’adresse fournie, ex. :  
   `\\nas.techflex.lan\partage`  
   ou (si accès par IP) :  
   `\\192.168.1.100\partage`
5. Cochez **"Se reconnecter à l’ouverture de session"**.
6. Si demandé, entrer vos identifiants d’accès (fournis par l’entreprise).

✅ Le dossier partagé apparaîtra comme un lecteur dans "Ce PC".

> ℹ️ Attention : pour que cela fonctionne à distance, le **VPN doit être activé**.

---

## 3. Installation de Microsoft 365 (OneDrive, Teams, Outlook…)

### 🧩 Pourquoi ?
Microsoft 365 vous permet de travailler dans le cloud : mails, réunions, documents partagés (OneDrive, SharePoint), et messagerie instantanée (Teams).

### 📥 Téléchargement :

- Page officielle : [https://www.microsoft365.com/](https://www.microsoft365.com/)

### 🧭 Étapes :

1. Connectez-vous avec vos identifiants professionnels (adresse mail fournie par TechFlex).
2. Cliquez sur **"Installer les applications Office"**.
3. Lancez le fichier téléchargé et suivez les instructions.
4. Une fois installé, ouvrez les applications :
   - **OneDrive** : pour accéder à vos fichiers dans le cloud
   - **Outlook** : pour les emails professionnels
   - **Teams** : pour la communication interne
   - **Word / Excel / PowerPoint** : pour la bureautique

✅ Une icône OneDrive apparaîtra dans la barre des tâches. Elle doit être **en bleu (connectée)**.

---

## 4. Recommandations d’usage

| Action                  | Recommandé ? | Fréquence |
|-------------------------|--------------|-----------|
| Activer le VPN avant d’ouvrir le lecteur réseau | ✅ Oui | À chaque connexion distante |
| Travailler depuis OneDrive (cloud) | ✅ Oui | En continu |
| Sauvegarder localement sur le NAS | ✅ Oui (automatique via OneDrive ou manuel) | Si accès direct |
| Utiliser Teams pour les échanges pro | ✅ Oui | Quotidien |
| Travailler dans un lieu calme et privé | ✅ Oui | Toujours |
| Se connecter depuis un PC personnel | ⚠️ Toléré si protégé | Exceptionnel |

---

## 5. Assistance technique

En cas de blocage, contactez le service informatique de TechFlex :  
📧 **support@techflex.local**  
📞 **+33 1 23 45 67 89**

---

## ✅ Résumé des installations

| Élément à installer     | Obligatoire | Utilisateurs concernés |
|--------------------------|-------------|-------------------------|
| WireGuard VPN            | ✅ Oui      | Télétravailleurs        |
| Lecteur réseau (NAS)     | ✅ Oui      | Tous                    |
| Microsoft 365 (OneDrive, Outlook, Teams…) | ✅ Oui | Tous                    |
| Navigateur recommandé    | ⬜ Optionnel (Chrome, Edge) | Tous |

---
