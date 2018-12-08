# Berechtigungen auf dem Apache Server für Joomla!

Der Ordner `/var/www/html/joomla-cms` ist der, in dem meine Joomla-Dateien liegen. 
Dieser Ordner gehört dem Benutzer www-data und der Gruppe www-data. 
Der Webserver Apache2 läuft unter dem BEnutzer www-data in der Gruppe www-data.

Für das Öffnen im Browser ist das auch aussreichend. Ich möchte aber mit meinem Benutzer 
auch Dateien 
in meiner Entwicklungsumgebung bearbeiten können.  

Eine gefrickelte pfui Lösung wäre `chmod -R 777 /var/www/html/joomla-cms`. 
Damit darf jeder alles mit den Joomla! Dateien machen. Deshalb mache ich das nicht.  

In meiner lokalen Umgebung habe ich folgendes eingestellt: 
Ich habe im ersten Schritt alle Joomla!-Dateien meinem Benutzer zugeordnet. 

```
chown -R astrid:astrid /var/www/html/joomla-cms/
```

Im nächsten Schritt habe ich dann den Benutzer, 
unter dem Apache2 ausgeführt wird, geändert. 
Dazu habe ich die Datei `/etc/apache2/envvars` geändert. 
Dies habe ich mit dem Befehl `sudo gedit /etc/apache2/envvars` erreicht.  

Ganz genau habe ich den Text

```
export APACHE_RUN_USER=www-data	
export APACHE_RUN_GROUP=www-data
```
in 
```
export APACHE_RUN_USER=meinbenutzername	
export APACHE_RUN_GROUP=meinbenutzername
```
geändert.

Zur Erinnerung: 
Berechtigungen im Webprojekt Joomla! sollten immer so eingestellt sein:

```
find /var/www/html/joomla-cms/ -type d -exec chmod 755 {} \;
find /var/www/html/joomla-cms/ -type f -exec chmod 644 {} \;
```

Fertig, nun arbeitet der Webserver noch korrekt und ich selbst kann auch Datei 
bearbeiten.

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