# Script : Alerte espace disque NAS

## Objectif
Envoyer un mail d’alerte si l’espace disque utilisé dépasse un seuil critique.

## Script Bash

```bash
#!/bin/bash
THRESHOLD=90
USAGE=$(df -h /mnt/partage | awk 'NR==2 {gsub("%","",$5); print $5}')

if [ "$USAGE" -gt "$THRESHOLD" ]; then
  echo "ALERTE: NAS dépasse $THRESHOLD% d'utilisation." | mail -s "Alerte NAS" admin@techflex.local
fi
```

## Automatisation
- Ajouter dans une tâche cron quotidienne ou horaire.