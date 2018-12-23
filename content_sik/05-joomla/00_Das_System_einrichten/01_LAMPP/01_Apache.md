# Apache installieren und die Firewall aktualisieren

## Apache

Der Apache Webserver gehört zu den beliebtesten Webservern der Welt. 
Er ist gut dokumentiert und wird oft verwendet.

Ich habe Apache mit dem Paketmanager APT[^1] von Ubuntu installiert. 

> APT ist ein Paketmanagement-System, das im Bereich des Betriebssystems 
Debian GNU/Linux entstanden ist. Mittels APT ist es sehr einfach, 
Programmpakete zu suchen, zu installieren oder auch das ganze System 
auf den neuesten Stand zu bringen.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt update
OK:1 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease
OK:2 http://de.archive.ubuntu.com/ubuntu bionic InRelease                      
OK:3 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease              
OK:4 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease            
OK:5 http://security.ubuntu.com/ubuntu bionic-security InRelease               
OK:6 https://deb.nodesource.com/node_8.x bionic InRelease                      
Paketlisten werden gelesen... Fertig                                           
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Alle Pakete sind aktuell.
```

> `update` liest alle in der `/etc/apt/sources.list` und in `/etc/apt/sources.list.d/` 
eingetragenen Paketquellen neu ein. Diesen Schritt führe ich immer einem upgrade oder 
nach dem Hinzufügen einer neuen Quelle aus, 
um die aktuellsten Informationen zu den verfügbaren Paketen zu haben. `apt-get upgrade` 
bringt die installierten Pakete - wenn nötig - auf den neuesten Stand. 


Da `sudo apt update` ein `sudo`-Befehl ist, werden diese Operationen mit Root-Rechten 
ausgeführt. Ich werde nach dem Passwort meines Benutzers gefragt. Damit wird 
sichergestellt, dass ich mir dass alles gut überlege und auch wirklich 
apache2 installieren will.  

Sobald ich mein Passwort eingegeben habe, teilt APT mir mit, 
welche Pakete installiert werden sollen und wie viel zusätzlichen 
Speicherplatz diese Pakete benötigen - oder eben, dass alles aktuell ist. 

Mittels `sudo apt install apache2` starte ich dann die Installation on Apache.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install apache2
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  apache2-bin apache2-data apache2-utils libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap liblua5.2-0
Vorgeschlagene Pakete:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom
Die folgenden NEUEN Pakete werden installiert:
  apache2 apache2-bin apache2-data apache2-utils libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap liblua5.2-0
0 aktualisiert, 9 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 1.713 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 6.920 kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libapr1 amd64 1.6.3-2 [90,9 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libaprutil1 amd64 1.6.1-2 [84,4 kB]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libaprutil1-dbd-sqlite3 amd64 1.6.1-2 [10,6 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libaprutil1-ldap amd64 1.6.1-2 [8.764 B]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 liblua5.2-0 amd64 5.2.4-1.1build1 [108 kB]
Holen:6 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 apache2-bin amd64 2.4.29-1ubuntu4.4 [1.071 kB]
Holen:7 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 apache2-utils amd64 2.4.29-1ubuntu4.4 [83,5 kB]
Holen:8 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 apache2-data all 2.4.29-1ubuntu4.4 [160 kB]
Holen:9 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 apache2 amd64 2.4.29-1ubuntu4.4 [95,1 kB]
Es wurden 1.713 kB in 1 s geholt (1.860 kB/s).
Vormals nicht ausgewähltes Paket libapr1:amd64 wird gewählt.
(Lese Datenbank ... 164109 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../0-libapr1_1.6.3-2_amd64.deb ...
Entpacken von libapr1:amd64 (1.6.3-2) ...
Vormals nicht ausgewähltes Paket libaprutil1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../1-libaprutil1_1.6.1-2_amd64.deb ...
Entpacken von libaprutil1:amd64 (1.6.1-2) ...
Vormals nicht ausgewähltes Paket libaprutil1-dbd-sqlite3:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../2-libaprutil1-dbd-sqlite3_1.6.1-2_amd64.deb ...
Entpacken von libaprutil1-dbd-sqlite3:amd64 (1.6.1-2) ...
Vormals nicht ausgewähltes Paket libaprutil1-ldap:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../3-libaprutil1-ldap_1.6.1-2_amd64.deb ...
Entpacken von libaprutil1-ldap:amd64 (1.6.1-2) ...
Vormals nicht ausgewähltes Paket liblua5.2-0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../4-liblua5.2-0_5.2.4-1.1build1_amd64.deb ...
Entpacken von liblua5.2-0:amd64 (5.2.4-1.1build1) ...
Vormals nicht ausgewähltes Paket apache2-bin wird gewählt.
Vorbereitung zum Entpacken von .../5-apache2-bin_2.4.29-1ubuntu4.4_amd64.deb ...
Entpacken von apache2-bin (2.4.29-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket apache2-utils wird gewählt.
Vorbereitung zum Entpacken von .../6-apache2-utils_2.4.29-1ubuntu4.4_amd64.deb ...
Entpacken von apache2-utils (2.4.29-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket apache2-data wird gewählt.
Vorbereitung zum Entpacken von .../7-apache2-data_2.4.29-1ubuntu4.4_all.deb ...
Entpacken von apache2-data (2.4.29-1ubuntu4.4) ...
Vormals nicht ausgewähltes Paket apache2 wird gewählt.
Vorbereitung zum Entpacken von .../8-apache2_2.4.29-1ubuntu4.4_amd64.deb ...
Entpacken von apache2 (2.4.29-1ubuntu4.4) ...
libapr1:amd64 (1.6.3-2) wird eingerichtet ...
Trigger für ufw (0.35-5) werden verarbeitet ...
Trigger für ureadahead (0.100.0-20) werden verarbeitet ...
ureadahead will be reprofiled on next reboot
apache2-data (2.4.29-1ubuntu4.4) wird eingerichtet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
libaprutil1:amd64 (1.6.1-2) wird eingerichtet ...
Trigger für systemd (237-3ubuntu10.3) werden verarbeitet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
liblua5.2-0:amd64 (5.2.4-1.1build1) wird eingerichtet ...
libaprutil1-ldap:amd64 (1.6.1-2) wird eingerichtet ...
libaprutil1-dbd-sqlite3:amd64 (1.6.1-2) wird eingerichtet ...
apache2-utils (2.4.29-1ubuntu4.4) wird eingerichtet ...
apache2-bin (2.4.29-1ubuntu4.4) wird eingerichtet ...
apache2 (2.4.29-1ubuntu4.4) wird eingerichtet ...
Enabling module mpm_event.
Enabling module authz_core.
Enabling module authz_host.
Enabling module authn_core.
Enabling module auth_basic.
Enabling module access_compat.
Enabling module authn_file.
Enabling module authz_user.
Enabling module alias.
Enabling module dir.
Enabling module autoindex.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module filter.
Enabling module deflate.
Enabling module status.
Enabling module reqtimeout.
Enabling conf charset.
Enabling conf localized-error-pages.
Enabling conf other-vhosts-access-log.
Enabling conf security.
Enabling conf serve-cgi-bin.
Enabling site 000-default.
Created symlink /etc/systemd/system/multi-user.target.wants/apache2.service → /lib/systemd/system/apache2.service.
Created symlink /etc/systemd/system/multi-user.target.wants/apache-htcacheclean.service → /lib/systemd/system/apache-htcacheclean.service.
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
Trigger für systemd (237-3ubuntu10.3) werden verarbeitet ...
Trigger für ureadahead (0.100.0-20) werden verarbeitet ...
Trigger für ufw (0.35-5) werden verarbeitet ...
```

Das war schon alles: Apache ist nun installiert. Im nächsten Schritt wird nun die Firewall angepasst.

## Die Firewall anpassen, um Web-Datenverkehr zuzulassen.

Die UFW-Firewall[^2] ist aktiviert. Ich stelle sicher, dass meine 
Firewall HTTP- und HTTPS-Datenverkehr zulässt. 
Ich kann überprüfen, ob UFW ein Anwendungsprofil für Apache hat. Ich liste mir die 
verfügbaren Anwendungen wie folgt auf.

```
astrid@astrid-TravelMate-5760G:~$ sudo ufw app list
Verfügbare Anwendungen:
  Apache
  Apache Full
  Apache Secure
  CUPS
```

Wenn ich mir das Apache Full-Profil ansehe, sollte es zeigen, 
dass es Datenverkehr zu den Ports 80 (HTTP) und 443 (HTTPS) ermöglicht.

```
astrid@astrid-TravelMate-5760G:~$ sudo ufw app info "Apache Full"
Profil: Apache Full
Titel: Web Server (HTTP,HTTPS)
Beschreibung: Apache v2 is the next generation of the omnipresent Apache
web server.

Ports:
  80,443/tcp
```

So lasse ich HTTP- und HTTPS-Datenverkehr für dieses Profil zu:

```
astrid@astrid-TravelMate-5760G:~$ sudo ufw allow in "Apache Full"
Regeln aktualisiert
Regeln aktualisiert (v6)
```

Ich kann mir ansehen, ob alles gekappt hat. Ein einfacher Test ist 
das Öffnen des Stammverzeichnisses[^3] meines Apache im Webbrowser. Zum Beispiel mittels 
der Eingabe von `http://localhost` in die Adresszeile meines Webbrowsers. 
Wenn alles richtig ist sehe ich die Standard Apache-Webseite. 
Diese steht immer für Informations- und Testzwecke zur Verfügung. 
Die Ansicht im Browser sollte ungefähr so aussehen.

![Apache Standard Seite](../../media/1_Apache2_Ubuntu_Default_Page.png)

Dieser Schritt ist fertig: Apache ist nun installiert.

*[PHP]: PHP Hypertext PreProcessor
*[API]: Application Programmer Interface
*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
*[APT]: Advanced Packaging Tool
*[UFW]: Unkomplizierte Firewall

[^1]: https://de.wikipedia.org/w/index.php?title=Advanced_Packaging_Tool&oldid=180106874
[^2]: https://en.wikipedia.org/w/index.php?title=Uncomplicated_Firewall&oldid=862587330 und https://wiki.ubuntuusers.de/ufw/
[^3]: https://de.wikipedia.org/wiki/Stammverzeichnis
[^4]: https://wiki.ubuntuusers.de/Rechte/
[^5]: https://wiki.ubuntuusers.de/chmod/
[^6]: https://wiki.ubuntuusers.de/chown/
[^7]: https://wiki.ubuntuusers.de/Benutzer_und_Gruppen/
[^8]: https://wiki.ubuntuusers.de/adduser/
[^9]: https://wiki.ubuntuusers.de/Benutzer_und_Gruppen/