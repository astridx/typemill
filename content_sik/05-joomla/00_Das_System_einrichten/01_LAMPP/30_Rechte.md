# Berechtigungen auf dem Apache Server

Der Ordner `/var/www/html` ist der, auf den die Adresse `http://localhost/` verweist. 
Hier liegen in der Regel die Joomla-Dateien.  

Nun habe ich das Problem, dass der Benutzer von Apache den Namen `www-data` trägt, 
was dazu führt, dass weder `www-data` noch ich als normaler Benutzer Schreibrechte 
für `/var/www/html` besitze. Dieser Ordner wurde bei der Installation 
von LAMP mit `Rootrechten` angelegt und gehört daher `root`.  

Dies kann ich ändern, indem ich meinen aktullen Benutzer - ich arbeite hier gerade mit dem 
Benutzer astrid - im ersten Schritt der Gruppe `www-data` beitrete. Dies erreiche ich mithilfe 
des Befehls `sudo adduser astrid www-data && newgrp www-data`. 

> Mit dem Befehl `adduser` lege ich nicht nur einen neuen Benutzer an. 
Mit `adduser` werden auch weitere nötige Einstellungen vorgenommen. Beispielsweise 
das Zuordnen des Benutzers zu einer Gruppe[^8]. Die Informationen zur 
Benutzerveraltung[^9] im Wiki von Ubuntuusers sind meiner Meinung nach hilfreich, wenn man mit Linux startet.

```
astrid@astrid-TravelMate-5760G:~$ sudo adduser astrid www-data && newgrp www-data
[sudo] Passwort für astrid: 
Benutzer »astrid« wird der Gruppe »www-data« hinzugefügt …
Benutzer astrid wird zur Gruppe www-data hinzugefügt.
Fertig.
```

Anschließend ändere ich den Besitzer und die Gruppe 
des Verzeichnisses `/var/www/html` von `root` auf `www-data`. 
Danach gebe ich der Gruppe 
`www-data` Schreibrechte auf dieses Verzeichnis. Damit ich die Joomla-Dateien später dorthin 
kopieren kann.

> Der Befehl chmod[^5] dient zum Setzen der Dateirechte. 
Der Befehl chown[^6] dient zum Ändern des Dateibesitzers.
Die Rechte in einem Linux System sind meiner Meinung im Wiki von Ubuntuusers[^4] gut erklärt.   

```
astrid@astrid-TravelMate-5760G:~$ sudo chown www-data:www-data /var/www/html && sudo chmod 775 /var/www/html
```

Nun kann ich die Dateien der eigenen Webprojekte in einen entsprechenden Ordner 
unterhalb von `/var/www/html` kopieren. Ich `clone` hierzu das Git Repositiory 
`https://github.com/joomla/joomla-cms.git`. Mehr dazu im nächsten Kapitel.

Ich möchte für Joomla Erweiterungen entwickeln und eventuell beim Beheben von 
Fehlern helfen. Deshalb macht es Sinn, 
die Zugriffsrechte für die Joomla-Dateien nun so einzustellen, 
dass ich selbst und www-data Lese- und Schreibzugriff besitzen.

```
astrid@astrid-TravelMate-5760G:~$ sudo chown -R www-data:www-data /var/www/html
[sudo] Passwort für astrid: 
astrid@astrid-TravelMate-5760G:~$ sudo find /var/www/html -type d -exec chmod 775 '{}' \;
astrid@astrid-TravelMate-5760G:~$ sudo find /var/www/html -type f -exec chmod 664 '{}' \;
```


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