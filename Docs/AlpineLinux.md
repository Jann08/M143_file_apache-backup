# Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*

# Alpine Linux

Alpine Linux ist eine minimalistische, sicherheitsorientierte Linux-Distribution, die besonders für Container, Server und Embedded-Systeme geeignet ist. Alpine Linux ist sehr schlank, Performant und Recurcenarm. Daher gut geeignet für mein Projekt.

## Wiso Alpine Linux

- **Klein und leichtgewichtig:** Das Basissystem ist nur 270MB Gross.
- **Sicher:** Standardmässig kommen immer mal wieder Updates für erhöhte Sicherheit.
- **Paketverwaltung:** Verwendet `apk` als schnellen und einfachen Paketmanager. (Leider kein gewohntes APT)
- **Geeignet für Server:** Praktisch als Server da nur das Minimale installiert ist.
- **Rolling Release:** Stetig aktualisierte Pakete und Sicherheitsupdates.

![Alpine](https://raw.githubusercontent.com/Jann08/M143_nfs-apache-backup/main/imgs/Alpine.png)

## Links

- [Offizielle Webseite](https://alpinelinux.org/)
- [Dokumentation](https://wiki.alpinelinux.org/)
- [GitHub Repository](https://github.com/alpinelinux/aports)