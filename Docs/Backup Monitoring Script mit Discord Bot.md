# Backup Monitoring Script mit Discord Bot
**Modul M143** | **TBZ** | *Jann Neururer*

# Übersicht

Dieses Bash-Script überwacht den Status von Dateiserver-Backups und sendet bei Problemen automatische Benachrichtigungen über einen Discord Webhook.

# Funktionsweise

- **Recourcen Check:** Das Script prüft, ob im Backup-Verzeichnis /backup/fileserver innerhalb der letzten 24 Stunden neue Dateien erstellt wurden
- **Bei Erfolg:** Keine Aktion (Script läuft still)
- **Bei Fehler:** Sendet eine Fehlermeldung an den Discord-Channel


## Script

![Script](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Botmsg.png)


# Discord Bot Integration

## Bot-Nachricht
Bei einem Backup-Fehler sendet der Bot folgende Nachricht:
**`***Backup Fehler:*** Kein Backup heute!`**

## Webhook Konfiguration
- Die Webhook-URL wird in der Variable **`MEBHOOK`** gespeichert
- Nachrichten werden im JSON-Format mit application/json Content-Type gesendet
- Der Bot nutzt die Discord API für automatische Benachrichtigungen


## Automatisierung via Cronjob

### Cronjob-Einrichtung
**`0 3 * * * /backup/check_backup.sh`**
### Zeitplan

- **Ausführungszeit:** 03:00 Uhr täglich
- **Logik:** Wird nach Abschluss des Backup-Prozesses ausgeführt
- **Zweck:** Überprüfung des Backup-Status kurz nach der geplanten Backup-Zeit


## Erweiterungsmöglichkeiten

- Erweiterte Fehlerberichterstattung
- Detailierte Backup-Statistiken
- Mehrere Benachrichtigungskanäle
- Historische Auswertungen
- Retry-Mechanismen


## Links
- [Offizielle Webseite](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks)  
- [Dokumentation](https://discord.com/developers/docs/intro)  
- [GitHub Repository](https://github.com/topics/discord-webhooks)
