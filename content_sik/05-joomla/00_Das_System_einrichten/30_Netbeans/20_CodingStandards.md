# Coding Standards - Erste Schritte für Joomla

https://github.com/squizlabs/PHP_CodeSniffer


```
astrid@astrid-TravelMate-5760G:~$ sudo apt install php-codesniffer
[sudo] Passwort für astrid: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  linux-headers-4.15.0-13 linux-headers-4.15.0-13-generic
  linux-image-4.15.0-13-generic linux-image-extra-4.15.0-13-generic
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
Die folgenden NEUEN Pakete werden installiert:
  php-codesniffer
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 8 nicht aktualisiert.
Es müssen 443 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 3.521 kB Plattenplatz zusätzlich benutzt.
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 php-codesniffer all 3.2.3-1 [443 kB]
Es wurden 443 kB in 1 s geholt (781 kB/s).
Vormals nicht ausgewähltes Paket php-codesniffer wird gewählt.
(Lese Datenbank ... 211172 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../php-codesniffer_3.2.3-1_all.deb ...
Entpacken von php-codesniffer (3.2.3-1) ...
php-codesniffer (3.2.3-1) wird eingerichtet ...
Trigger für man-db (2.8.3-2ubuntu0.1) werden verarbeitet ...
astrid@astrid-TravelMate-5760G:~$ phpcs -version
ERROR: option "-r" not known

Run "phpcs --help" for usage information
```

```
astrid@astrid-TravelMate-5760G:~$ phpcs --version
PHP_CodeSniffer version 3.2.3 (stable) by Squiz (http://www.squiz.net)
```
```
astrid@astrid-TravelMate-5760G:~$ phpcbf --version
PHP_CodeSniffer version 3.2.3 (stable) by Squiz (http://www.squiz.net)
```


Ich finde CodeSniffer nun im Verzeichnis `/usr/bin/phpcs`. 

Die installierten Coding Standards kann ich mir mit dem Befehl `/usr/bin/phpcs -i` 
ansehen.

```
/usr/bin/phpcs -i
The installed coding standards are MySource, Zend, Squiz, PEAR, PSR2 and PSR1
astrid@astrid-TravelMate-5760G:/usr/share/php/PHP/CodeSniffer/src/Standards$ 
```


















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