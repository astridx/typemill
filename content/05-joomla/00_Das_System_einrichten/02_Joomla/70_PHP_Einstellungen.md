# Berechtigungen auf dem Apache Server für Joomla!


`upload_max_filesize`[^1] ist das Limit einer einzelnen Datei. `post_max_size`[^2] 
ist die Grenze des gesamten Uploads, der mehrere Dateien enthalten kann. 
Diese Werte sind in einer Standardkonfiguration oft sehr niedrig angesetzt. 
Joomla meldet einem dann teilweise den Fehler 

> Es gibt einen Fehler beim Hochladen dieser Datei auf den Server. 
Maximale PHP-Dateihochladegröße zu klein: Sowohl der Wert für „upload_max_filesize“, 
als auch für „post_max_size“ muss in der php.ini und/oder der .htaccess-Datei 
definiert werden.“

Bei `post_max_size = 20M` und `upload_max_filesize = 6M` können 
Sie bis zu 3 Dateien mit jeweils 6 MB hochladen. 
Wenn stattdessen `post_max_size = 6 MB` und `upload_max_filesize = 20 MB` beträgt, 
können Sie nur eine 6 MB Datei hochladen.

## Wie passen Sie die Werte an?

Zunächst müssen Sie Ihre `php.ini`-Datei suchen. 
In diesem Beispiel befindet sich die php.ini-Datei unter der Adresse 
`/etc/php/7.2/apache2/php.ini`.

Öffnen Sie diese Datei zum Bearbeiten mithilfe des Befehls

```
sudo gedit /etc/php/7.2/apache2/php.ini
```

Suchen Sie nach dem Eintrag `upload_max_filesize` und ändern Sie den Wert in 64M (für 64 MB).


```
...
upload_max_filesize = 2M
...
```

Suchen Sie nach dem Eintrag post_max_size und ändern Sie den Wert in 64M (für 64 MB).

```
...
post_max_size = 8M
...
```


Starten Sie Apache neu, um die Änderungen anzuwenden.


```
sudo systemctl restart apache2
```


*[PHP]: PHP Hypertext PreProcessor
*[API]: Application Programmer Interface
*[HTML]: Hyper Text Markup Language
*[W3C]: World Wide Web Consortium
*[APT]: Advanced Packaging Tool
*[UFW]: Unkomplizierte Firewall

[^1]: http://php.net/upload-max-filesize
[^2]: http://php.net/post-max-size