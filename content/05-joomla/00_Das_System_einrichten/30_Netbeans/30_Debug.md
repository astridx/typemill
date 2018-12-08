# Debug - Erste Schritte für Joomla

http://localhost/info.php

http://purencool.com/installing-xdebug-on-ubuntu

```
astrid@astrid-TravelMate-5760G:~$ sudo apt-get install php-xdebug 
[sudo] Passwort für astrid: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  linux-headers-4.15.0-13 linux-headers-4.15.0-13-generic
  linux-image-4.15.0-13-generic linux-image-extra-4.15.0-13-generic
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
Die folgenden NEUEN Pakete werden installiert:
  php-xdebug
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 8 nicht aktualisiert.
Es müssen 379 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 1.641 kB Plattenplatz zusätzlich benutzt.
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 php-xdebug amd64 2.6.0-0ubuntu1 [379 kB]
Es wurden 379 kB in 0 s geholt (1.202 kB/s).
Vormals nicht ausgewähltes Paket php-xdebug wird gewählt.
(Lese Datenbank ... 211706 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../php-xdebug_2.6.0-0ubuntu1_amd64.deb ...
Entpacken von php-xdebug (2.6.0-0ubuntu1) ...
php-xdebug (2.6.0-0ubuntu1) wird eingerichtet ...
astrid@astrid-TravelMate-5760G:~$ sudo gedit /etc/php/7.2/apache2/php.ini 
```




sudo gedit /etc/php/7.2/apache2/php.ini 


```
; Added for xdebug
zend_extension="/usr/lib/php/20170718/xdebug.so"
xdebug.remote_enable=1
xdebug.remote_handler=dbgp
xdebug.remote_mode=req
xdebug.remote_host=127.0.0.1
xdebug.remote_port=9000
```

sudo systemctl restart apache2 


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