# rsync Backup Script

**Modul M143** | **TBZ** | *Jann Neururer*


## Speicherort

- Script: /backup/rsync_backup.sh
- Logs: /backup/logs/rsync_(Datum).log
- Verschlüsselte Backups: /backup/encrypted/

## Funktionsweise

### 1. Rsync-Backup

- Verbindung zu Quellservern per SSH
- Übertragung nur geänderter Daten
- Beibehaltung der Dateiberechtigungen
- Protokollierung aller Aktivitäten

### 2. Verschlüsselung

- Komprimierung mit tar
- Verschlüsselung mit GnuPG (GPG)
- Automatische Bereinigung temporärer Dateien

## Voraussetzungen
- [Installierte Packete](Umsetzung.md#installierte-packages)

SSH-Zugriff konfigurieren
- [SSH Zugriff](Umsetzung.md#ssh-keys-generieren)

## GPG-Schlüssel einrichten

- GPG-Schlüsselpaar generieren
**`gpg --full-generate-key`**
- Öffentlicher Schlüssel exportieren 
**`gpg --export --armor jann.neururer@edu.tbz.ch > public.key`**

## Backup Script unverschlüsselt
Dieses Script Ist sehr minimal gehalten und führ das Loggin per SSH auf die Server durch, kopiert die daten und Speichert sie auf den Backup Server. Dazu wird eine Kleine Log Datei geschrieben.
- Output des Logs:

![logklein](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/sentproof.png)

- Script datei:

![Backupscript](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Backupscript.png)


## Backup Script verschlüsselt
Ich habe mich dazu entschieden das ganze noch zu verschlüsseln da dies mehr sicherheit gibt. Das erweiterte Script erstellt Folders, Loggt SSH ein Koppiert die Daten in den Temporären Folder verschlüsselt diese mit GPG, zieht diese auf Backupsrv und löscht den Temp folder. Jede aktion wird in die Logg datei geschrieben.
- [Log der verschlüsselten version](/rsync_2025-10-24_11-53.log)
