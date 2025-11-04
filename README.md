# Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*

## MVP Ziel (Minimum Viable Product)
Eine vollautomatisierte, sichere und getestete Backup-Lösung für zwei Linux-Server einrichten:
1.  Ein **Fileserver**
2.  Ein **Webserver** (Apache)

Die Backups werden auf einem dritten, dedizierten **Backup-Server** gespeichert.

## Projektarchitektur
Einfaches Drei-Server-Setup: Debian Servers
- **`filesrv`** (IP: `192.168.169.129`): Hostet den Filesrv.
- **`websrv`** (IP: `192.168.169.130`): Hostet Apache-Websites.
- **`backsrv`** (IP: `192.168.169.131`): Backup-Server.

Alle Server sind minimale Linux-VMs ohne GUI, Alle vms laufen auf einem 90GB grossen Disc Partition.

---

## MVP Aufgaben / Checkliste

### Vorbereitung
- [x] **Netzwerk erstellen (Hostnet)
- [x] **Drei VMs erstellen** (`fileserver`, `webserver`, `backup`) mit festen IPs.
- [x] **Netzwerkkonnektivität testen** (z.B. `ping 8.8.8.8` vom `webserver` und `backup` aus).
- [x] **Einen Schnappschuss von allen VMs** im sauberen Grundzustand machen. (KRITISCH FÜR FALLBACKS!)

### Phase 1: Service-Installation & Konfiguration

#### `fileserver.vm.local` erstellen mit (IP: 192.168.169.129):
- [x] **Mit dem Host Netzwerk verbinden**
- [x] **Backupclient downloaden**

#### `webserver.vm.local` erstellen mit (IP: 192.168.169.130):
- [x] **Mit dem Host Netzwerk verbinden**
- [x] **Apache2 Webserver installieren:**

#### `backup.vm.local` erstellen mit (IP: 192.168.169.131):
- [x] **Backup Applikation Downloaden**
- [x] **Backup Verzeichnisse festlegen**

#### `SSH Keys` Generieren für Passwort loser Zugriff auf den Backup Server:
- [x] **Key Pairs generieren**
- [x] **Die Maschienen über die Keys verbinden**

#### `Cron` durch einen Cronjob das ganze backup automatisieren:
- [x] **Script Backup?**

#### `Wiederherstellung` testen durch auf dem fileserver Daten wiederherstellen:
- [x] **Dateien vom Backup server auf den Fileserver wiederherstellen und auf vollständigkeit prüfen**

## Erweiterungsmöglichkeiten
- [x] **2x Backup Server für Redundanz**
- [x] **Cron Job durch System Timer ersetzen(moderner)**
- [ ] **Automatisierte Konfiguration von vms durch Script oder Ansible**

# Produkt:
- [Zusammenfassung des Gemachten](Docs/Umsetzung.md#backup-lösung-für-linux-fileserver-und-web-service)
- [Discord Bot](Docs/Backup%20Monitoring%20Script%20mit%20Discord%20Bot.md)
- [Backup Script](Docs/rsync%20Backup%20Script.md)
- [Log Dateien](Docs/rsync_2025-10-24_11-53.log)
- [Entscheidung](Docs/Entscheidungen.md)

## NetPlan

![Network](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Diagramm3.png)


