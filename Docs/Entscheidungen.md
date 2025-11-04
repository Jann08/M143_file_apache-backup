# Wiso habe ich was gewählt?
**Modul M143** | **TBZ** | *Jann Neururer*


## 1. Statische IPs
**Grund:** In einer VMware-Umgebung mit NAT-Netzwerk bleiben die IPs konsistent, was die Automatisierung vereinfacht und sicherstellt, dass Server immer zuverlässig miteinander kommunizieren können.

## 2. Rsync
**Grund:** Rsync ist eine effiziente Lösung für Backups, da es nur geänderte Daten überträgt und nicht jedes Mal alle Dateien kopiert. Dadurch wird die Netzwerkbelastung minimiert und die Backup-Zeit verkürzt.

**Zusatz:** Rsync bietet viele Anpassungsoptionen, wie das Beibehalten von Dateiberechtigungen und detaillierte Protokollierung, was die Wiederherstellung erleichtert.

## 3. SSH Keys
**Grund:**
- **Automatisierung:** SSH-Keys ermöglichen passwortlose Verbindungen, was die Einrichtung von Cronjobs und automatisierten Backups vereinfacht.
- **Sicherheit:** Sie sind sicherer als Passwörter, da sie nicht abgefangen werden können und einen höheren Schutz gegen Brute-Force-Angriffe bieten.
- **Effizienz:** Einmal eingerichtet, sind sie dauerhaft nutzbar und reduzieren den Verwaltungsaufwand.

## 4. Verschlüsselung mit GnuPG (GPG)
**Grund:**
- **Datensicherheit:** Durch die Verschlüsselung mit GPG werden sensible Geschäftsdaten vor unbefugtem Zugriff geschützt, selbst bei einem Diebstahl des Backup-Servers.
- **Compliance:** Die Verschlüsselung hilft, rechtliche Anforderungen wie Datenschutzgesetze (DSG) einzuhalten.
- **Flexibilität:** Die Daten können bei Bedarf entschlüsselt und wiederhergestellt werden, ohne die Dateiberechtigungen zu verlieren.

## 5. Cronjobs für Automatisierung
**Grund:**
- **Zeitersparnis:** Automatisierte Backups und Statusprüfungen laufen ohne manuelle Eingriffe.
- **Effizienz:** Backups werden nachts durchgeführt, wenn die Server weniger ausgelastet sind, was die Performance der Systeme während der Arbeitszeit nicht beeinträchtigt.
- **Regelmäßigkeit:** Tägliche Backups bieten einen guten Schutz gegen Datenverluste und stellen sicher, dass immer eine aktuelle Kopie der Daten verfügbar ist.

## 6. Discord Bot für Monitoring
**Grund:**
- **Automatische Benachrichtigung:** Der Discord Bot informiert über den Status der Backups und warnt bei Problemen. Das spart Zeit und stellt sicher, dass du schnell reagieren kannst.
- **Integration:** Discord ist ein praktisches Tool für Benachrichtigungen, da es einfach einzurichten ist und in Echtzeit arbeitet.
- **Fehlererkennung:** Der Bot prüft, ob neue Dateien erstellt wurden, und meldet Probleme, wenn kein Backup erfolgt ist.

## 7. Wiederherstellung mit Rsync und GPG
**Grund:**
- **Flexibilität:** Mit Rsync und GPG können Daten direkt auf die Quellserver zurückgespielt und entpackt werden.
- **Sicherheit:** Die Wiederherstellung erfolgt über eine verschlüsselte Verbindung und entschlüsselt die Daten nur auf dem Zielserver.
- **Effizienz:** Rsync überträgt nur die notwendigen Daten, was die Wiederherstellungszeit verkürzt.
