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
- Installierte Pakete
[Zur Installationsanleitung](Docs/Umsetzung.md#installierte-packages)
