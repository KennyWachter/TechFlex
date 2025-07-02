# Script : Surveillance de la connexion VPN

## Objectif
Vérifier régulièrement la connectivité VPN et enregistrer les résultats dans un fichier log.

## Script Bash

```bash
#!/bin/bash
LOG="/var/log/wireguard_check.log"
DATE=$(date '+%Y-%m-%d %H:%M:%S')

if ping -c 1 192.168.1.1 >/dev/null; then
    echo "$DATE : VPN OK" >> $LOG
else
    echo "$DATE : VPN DOWN" >> $LOG
fi
```

## Automatisation
- Planifier le script avec un cron toutes les 10 minutes :

```bash
*/10 * * * * /bin/bash /chemin/check_vpn.sh
```