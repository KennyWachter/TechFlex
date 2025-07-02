# Script : Montage automatique du lecteur réseau (Windows)

## Objectif
Connecter automatiquement le lecteur réseau NAS au démarrage de session, uniquement si le VPN est actif.

## Script PowerShell

```powershell
$lettre = "Z:"
$chemin = "\\nas.techflex.lan\partage"

# Vérifie si le lecteur existe déjà
if (-not (Test-Path $lettre)) {
    if (Test-Connection -ComputerName "nas.techflex.lan" -Count 1 -Quiet) {
        New-PSDrive -Name "Z" -PSProvider FileSystem -Root $chemin -Persist
    }
}
```

## Mise en place
- Copier ce script dans un fichier `.ps1`
- L’ajouter dans le dossier de démarrage Windows (`shell:startup`)