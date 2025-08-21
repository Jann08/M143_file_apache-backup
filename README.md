# Enterprise Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*

## MVP Ziel (Minimum Viable Product)
Eine vollautomatisierte, sichere und getestete Backup-Lösung für zwei Linux-Server einrichten:
1.  Ein **Fileserver** (NFS)
2.  Ein **Webserver** (Apache)

Die Backups werden auf einem dritten, dedizierten **Backup-Server** mit **BorgBackup** gespeichert. Borg sorgt für effiziente, deduplizierte und versionierte Archive.

## Projektarchitektur
Einfaches Drei-Server-Setup:
- **`fileserver.vm.local`** (IP: `192.168.100.10`): Hostet NFS-Freigaben.
- **`webserver.vm.local`** (IP: `192.168.100.11`): Hostet Apache-Websites.
- **`backup.vm.local`** (IP: `192.168.100.20`): Dedizierter Backup-Server.

Alle Server sind minimale Linux-VMs ohne GUI, Alle vms laufen auf einem 90GB grossen Disc Partition.

---

## MVP Aufgaben / Checkliste

### Phase 0: Vorbereitung
- [ ] **Netzwerk erstellen (Hostnet)
- [ ] **Drei VMs erstellen** (`fileserver`, `webserver`, `backup`) mit festen IPs.
- [ ] **Netzwerkkonnektivität testen** (z.B. `ping 192.168.100.10` vom `webserver` und `backup` aus).
- [ ] **Einen Schnappschuss von allen VMs** im sauberen Grundzustand machen. (KRITISCH FÜR FALLBACKS!)

### Phase 1: Service-Installation & Konfiguration

#### `fileserver.vm.local` erstellen mit (IP: 10):
- [ ] **Mit dem Host Netzwerk verbinden**
- [ ] **NFS Server installieren:**

#### `webserver.vm.local` erstellen mit (IP: 11):
- [ ] **Mit dem Host Netzwerk verbinden**
- [ ] **NFS Client Installieren:**
- [ ] **Apache2 Webserver installieren:**

#### `backup.vm.local` erstellen mit (IP: 20):
- [ ] **Backup Applikation Downloaden**
- [ ] **Backup Verzeichnisse festlegen**

#### `SSH Keys` Generieren für Passwort loser Zugriff auf den Backup Server:
- [ ] **Key Pairs generieren**
- [ ] **Die Mashcienen über die Keys verbinden**

#### `Cron` durch einen Cronjob das ganze backup automatisieren:
- [ ] **Script Backup?**

#### `Wiederherstellung` testen durch auf dem fileserver Daten wiederherstellen:
- [ ] **Dateien vom Backup server auf den Fileserver wiederherstellen und auf vollständigkeit prüfen**

## Erweiterungsmöglichkeiten
- [ ] **Backups verschlüsseln**
- [ ] **2x Backup Server für Redundanz**
- [ ] **Mailserver für monitoring benachrichtigung**
- [ ] **Cloud Speichern**
- [ ] **Cron Job durch System Timer ersetzen(moderner)**
- [ ] **Automatisierte Konfiguration von vms durch Script oder Ansible**

##Projekt Struktur

├── README.md              # Diese Datei

├── docs/                  # Detaillierte Dokumentation

│   ├── Doku.md

│   ├── installationen.md

│   └── wiederherstellung.md

├── scripts/               # Alle verwendeten Skripte

│   ├── cronjob.sh

│   └── config.sh
└── assets/                # Screenshots, etc

    └── Netzwerkplan.png


