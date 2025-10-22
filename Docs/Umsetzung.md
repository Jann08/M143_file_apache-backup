# Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*


## Architektur

![topo](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/topo.png)

- **`Zentrale Verwaltung`** Durch diese strucktur hat mein Backupserver zugriff auf alle Quellsysteme was hier notwendig ist.
- **`Isolation`** Dazu ist bei einemm Problem mit einem Server der andere nicht betroffen.
  - **`Redundanz`** Der backsrv2 sichert die Backups von backsrv das gitb eine zweite Sicherungsebene.
## Konfiguration

- **`filesrv`** (IP: `192.168.169.129`): Hostet den Filesrv.
- **`websrv`** (IP: `192.168.169.130`): Hostet Apache-Websites.
- **`backsrv`** (IP: `192.168.169.131`): Backup-Server.
- **`backsrv2`** (IP: `192.168.169.132`): Sekundärer Backup-Server

Warum statische IPs? In einer VMware-Umgebung mit NAT-Netzwerk bleiben die IPs konsistent, was die Automatisierung vereinfacht.

## Installierte Packages

### Auf allen Servern
**`sudo apt install rsync openssh-server`**
rsync hab ich gewählt weil es effizient ist - nur Änderungen werden übertragen, nicht jedes Mal alle Daten.
openssh-server: Ermöglicht mir sichere Verbindungen zwischen den Servern

### Nur auf Webserver
**`sudo apt install apache2`**
apache2: habe ich gewählt da es ein sehr Zuverlässiger Webserver ist und es dazu Massenhaft an Dokumentationen gibt.

## SSH Keys
Ich habe mich für das benutzen von SSH Keys auf grund dieser Punkte entschieden:

- **`Automatisierung`** Cronjobs können ohne Passworteingabe laufen
- **`Sicherheit`** SSH Keys sind sicherer als Passwörter
- **`Praktikabel`** Einmal einrichten, dauerhaft nutzbar
- 
# Auf Backup Server die ssh keys erstellen und direkt auf die anderen 2 server übertragen.

**`ssh-keygen -t ed25519 -f ~/.ssh/backup_key -N ""`**
**`ssh-copy-id -i ~/.ssh/backup_key ladmin@192.168.169.129`**
**`ssh-copy-id -i ~/.ssh/backup_key ladmin@192.168.169.130`**

## Backup script erstellen
Speicherort: /backup/rsync_backup.sh

Das Script auf den Backupservern verbindet sich per SSH zu den Servern. Es überträgt nur Daten die Geändert wurden, und Protokolliert alles in den Logs und die Dateiberechtigungen bleiben die selben.

Ich benutze rsync da es sehr effizient ist, es werden keine schon vorhandenen Daten übertragen und es giebt viele Optionen für anpassungen.




## Cronjob
Täglich um 2 uhr wird ein Backup der Server gestartet.

**`0 2 * * * /backup/rsync_backup.sh`**

Das Backup wird um 2 Uhr nachts gemacht da gibt es weniger auslastung auf den Servern perfekt für das Backup.
Tägliche Backups sind wichtig da dies guten schutz gegen Datenverluste bietet.

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
