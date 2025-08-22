#Backup-Lösung für Linux Fileserver und Web-Service

**Modul M143** | **TBZ** | *Jann Neururer*

## NFS (Network File System)
**`NFS version 2 (NFSv2)`**

NFSv2 Ist die Älteste version und die am meisten verbreitete, supportete Version. Es läuft über UDP in einem IP Netzwerk. Somitt können alle befugten benutzer im Netzwerk darauf zugreifen.
Vor der Datenübertragung baut UDP keine verbindung auf, das ist praktisch, da Verbindungen dadurch shcneller gemacht werden können. Jedoch können UDP Clients weiterhin anfragen auf de Server senden auch wen dieser ausser betrieb ist.

**`NFS version 3 (NFSv3)`**
NFSv3 unterstütst asynchrone Schreibvorgänge. Das ermöglicht dem server die richtigen Richtlienien für die Synchronisierung von Daten festzulegen. Es wird vor dem final Commit eine synchronisation durchgeführt, dies dient zum besseren Buffering.
Ausserdem ist es effizienter und man kann durchschnittlich auf 2GB Daten zugreifen durch 64Bit Dateigrösse.

**`NFS version 4 (NFSv4)`**
NFSv4 ist die neusste Version des NFS Prottokolls. Diese version kann durch Firewalls durch Arbeiten. Dazu wird TCP verwendet und die verbindung wird zwischen einer Anwendung und einer IP hergestellt. Bei Datenverlust werden nur die verlorenen Dateien erneut übertragen und der Server akzeptiert befehle über den TCP port. 

![NFS](imgs/NFS.png)