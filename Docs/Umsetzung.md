# Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*


## Architektur

Fileserver (filesrv) ───┐
                        │
Webserver (websrv) ─────┤─── Backup Server (backsrv)

## Konfiguration

- **`filesrv`** (IP: `192.168.169.129`): Hostet den Filesrv.
- **`websrv`** (IP: `192.168.169.130`): Hostet Apache-Websites.
- **`backsrv`** (IP: `192.168.169.131`): Backup-Server.
- **`backsrv2`** (IP: `192.168.169.132`): Backup-Server2.(Backupt den ersten Backup server, Gleiches Prinzip nur backupt er die Gebackupten Ordner von backsrv.)

## Installierte Packages

### Auf allen Servern
**`sudo apt install rsync openssh-server`**

### Nur auf Webserver
**`sudo apt install apache2`**

## SSH Keys

# Auf Backup Server die ssh keys erstellen und direkt auf die anderen 2 server übertragen.

**`ssh-keygen -t ed25519 -f ~/.ssh/backup_key -N ""`**
**`ssh-copy-id -i ~/.ssh/backup_key ladmin@192.168.169.129`**
**`ssh-copy-id -i ~/.ssh/backup_key ladmin@192.168.169.130`**

## Backup script erstellen
/backup/rsync_backup.sh

das backup wird durch ein script ausgeführt, das script verbindet vom Backupsrv mit ssh auf die anderen Server und führt das backup aus, indem es die vorgegebenen ordner rüberladet.

## Cronjob
Täglich um 2 uhr wird ein Backup der Server gestartet.

**`0 2 * * * /backup/rsync_backup.sh`**

## Wiederherstellung

Um das Backup wiederherzustellen kann man die Dateien wieder zurückholen indem man die Datei angibt oder das ganze verzeichniss angibt.

Auf dem Backupserver: **`rsync -av -e "ssh -i ~/.ssh/backup_key" /backup/fileserver/geschaeftsdaten.txt ladmin@192.168.169.129:/backup/`**

## Test und Validierung

### Erfolgreicher Backup Test:
![command](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Backupcommand.png)

![Backupproof](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/backup.png)

![sentproof](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/sentproof.png)

### Backup Script:
![Backupscript](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Backupscript.png)

### Wiederherstellung:

![Wiederherstellung](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/wiederherstellung.png)