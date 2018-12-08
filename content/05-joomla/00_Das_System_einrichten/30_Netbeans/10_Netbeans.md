# Ubuntu 18.04 - Netbeans - Erste Schritte für Joomla

## Wie installierte ich NetBeans IDE 8.2 in Ubuntu 18.04

NetBeans ist eine Open-Source-integrierte Entwicklungsumgebung, 
die ein sehr leistungsfähiges Java-Anwendungsframework bietet. 
Ich nutze Netbeans auch für die Arbeit mit Joomla. 
Hier beschreibe ich wie ich NetBeans IDE 8.2 in Ubuntu 18.04 installiert habe.

### Installation

Zuerst muss ich Java auf meinem Rechner installieren, 
also füge ich das PPA Repo von Java wie folgt hinzu.

```
root @ linuxhelp1: ~ # add-apt-repository ppa:webupd8team/java
```

Jetzt muss ich das System-Repository aktualisieren.

```
root @ linuxhelp1: ~ # apt-get update
```

Nun installiere ich Java.

```
root @ linuxhelp1: ~ # apt-get installieren oracle-java8-installer
```

Ich lade mit dem Befehl wget ein Netbeans-Paket vom Terminal herunter.

```
root @ linuxhelp1: ~ # wget -c http://download.netbeans.org/netbeans/8.2/final/bundles/netbeans-8.2-linux.sh
```

Nachdem der Download abgeschlossen ist, navigiere ich zu dem Verzeichnis, 
in das der NetBeans IDE Installer heruntergeladen wurde. Ich mache 
das Installer-Skript ausführbar und starten Sie die Installation.

```
root @ linuxhelp1: ~ # chmod + x netbeans-8.2-linux.sh
root @ linuxhelp1: ~ # ./netbeans-8.2-linux.sh
```

Auf dem Bildschirm wird der Installationsassistent angezeigt. Ich werde mit Fragen 
durch die Installation geführt. Ich habe überall die Standardwerte übernommen.


Wenn alles fertig ist, kann ich über die Schalftläche zum Anzeigen der Anwendungen in 
Ubuntu 18.04 auf die Anwendung Netbeans zugreifen.


![Apache Standard Seite](../../media/6_netbeans.png)


*[PHP]: PHP Hypertext PreProcessor
*[API]: Application Programmer Interface
*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
*[APT]: Advanced Packaging Tool
*[UFW]: Unkomplizierte Firewall

[^1]: https://de.wikipedia.org/w/index.php?title=Advanced_Packaging_Tool&oldid=180106874
[^2]: https://en.wikipedia.org/w/index.php?title=Uncomplicated_Firewall&oldid=862587330 und https://wiki.ubuntuusers.de/ufw/

[^3]: https://fontawesome.com
[^4]: https://github.com/gulp-community/gulp-concat
[^5]: https://github.com/dlmanning/gulp-sass
[^6]: https://github.com/terinjokes/gulp-uglify
[^7]: http://getbootstrap.com/docs/4.0/components/navbar/
[^8]: http://html-ipsum.com
[^9]: http://getbootstrap.com/docs/4.1/components/navbar/