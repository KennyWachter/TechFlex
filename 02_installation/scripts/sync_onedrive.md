# Script : Synchronisation NAS ↔ OneDrive (manuelle)

## Objectif
Lancer manuellement une synchronisation entre un dossier NAS local et OneDrive via `rclone`.

## Commande rclone

```bash
rclone sync /mnt/partage/onedrive remote:TechFlex --log-file=/var/log/rclone.log
```

## Pré-requis
- Configuration préalable de `rclone` avec un remote nommé `remote:` pointant vers OneDrive (`rclone config`)