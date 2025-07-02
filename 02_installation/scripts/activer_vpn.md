# Script : Lancement automatique de WireGuard (Windows)

## Objectif
Activer automatiquement le tunnel VPN WireGuard à la connexion utilisateur.

## Script Batch

```batch
@echo off
cd "C:\Program Files\WireGuard"
start wireguard.exe /quiet /tunnel "TechFlex VPN"
```

## Mise en place
- Enregistrer ce script en `.bat`
- Le placer dans le dossier `shell:startup` de Windows