# P H P

PHP ist die Komponente meiner Installation, die meine Joomla Code verarbeitet, 
um dynamischen Inhalt anzuzeigen. 
PHP kann 
* Skripte ausführen, 
* eine Verbindung zu meiner MySQL-Datenbanken herstellen um Informationen zu erhalten und  
* den verarbeiteten Inhalt zur Anzeige an den Web-Server übergeben.

Ich verwende wieder APT, um PHP zu installieren. 
Dieses Mal füge ich zusätzlich einige Hilfspakete hinzu, damit mein PHP-Code unter 
dem Apache-Server läuft und mit meiner MySQL-Datenbank kommunizieren kann.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install php libapache2-mod-php php-mysql
[sudo] Passwort für astrid: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libapache2-mod-php7.2 php-common php7.2 php7.2-cli php7.2-common php7.2-json
  php7.2-mysql php7.2-opcache php7.2-readline
Vorgeschlagene Pakete:
  php-pear
Die folgenden NEUEN Pakete werden installiert:
  libapache2-mod-php libapache2-mod-php7.2 php php-common php-mysql php7.2
  php7.2-cli php7.2-common php7.2-json php7.2-mysql php7.2-opcache
  php7.2-readline
0 aktualisiert, 12 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 3.975 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 17,6 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 php-common all 1:60ubuntu1 [12,1 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-common amd64 7.2.10-0ubuntu0.18.04.1 [878 kB]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-json amd64 7.2.10-0ubuntu0.18.04.1 [18,8 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-opcache amd64 7.2.10-0ubuntu0.18.04.1 [165 kB]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-readline amd64 7.2.10-0ubuntu0.18.04.1 [12,1 kB]
Holen:6 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-cli amd64 7.2.10-0ubuntu0.18.04.1 [1.405 kB]
Holen:7 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libapache2-mod-php7.2 amd64 7.2.10-0ubuntu0.18.04.1 [1.349 kB]
Holen:8 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libapache2-mod-php all 1:7.2+60ubuntu1 [3.212 B]
Holen:9 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2 all 7.2.10-0ubuntu0.18.04.1 [9.248 B]
Holen:10 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 php all 1:7.2+60ubuntu1 [3.084 B]
Holen:11 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-mysql amd64 7.2.10-0ubuntu0.18.04.1 [118 kB]
Holen:12 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 php-mysql all 1:7.2+60ubuntu1 [2.004 B]
Es wurden 3.975 kB in 1 s geholt (2.907 kB/s).
Vormals nicht ausgewähltes Paket php-common wird gewählt.
(Lese Datenbank ... 165082 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../00-php-common_1%3a60ubuntu1_all.deb ...
Entpacken von php-common (1:60ubuntu1) ...
Vormals nicht ausgewähltes Paket php7.2-common wird gewählt.
Vorbereitung zum Entpacken von .../01-php7.2-common_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-common (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php7.2-json wird gewählt.
Vorbereitung zum Entpacken von .../02-php7.2-json_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-json (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php7.2-opcache wird gewählt.
Vorbereitung zum Entpacken von .../03-php7.2-opcache_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-opcache (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php7.2-readline wird gewählt.
Vorbereitung zum Entpacken von .../04-php7.2-readline_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-readline (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php7.2-cli wird gewählt.
Vorbereitung zum Entpacken von .../05-php7.2-cli_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-cli (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket libapache2-mod-php7.2 wird gewählt.
Vorbereitung zum Entpacken von .../06-libapache2-mod-php7.2_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket libapache2-mod-php wird gewählt.
Vorbereitung zum Entpacken von .../07-libapache2-mod-php_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von libapache2-mod-php (1:7.2+60ubuntu1) ...
Vormals nicht ausgewähltes Paket php7.2 wird gewählt.
Vorbereitung zum Entpacken von .../08-php7.2_7.2.10-0ubuntu0.18.04.1_all.deb ...
Entpacken von php7.2 (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php wird gewählt.
Vorbereitung zum Entpacken von .../09-php_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von php (1:7.2+60ubuntu1) ...
Vormals nicht ausgewähltes Paket php7.2-mysql wird gewählt.
Vorbereitung zum Entpacken von .../10-php7.2-mysql_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-mysql (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php-mysql wird gewählt.
Vorbereitung zum Entpacken von .../11-php-mysql_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von php-mysql (1:7.2+60ubuntu1) ...
php-common (1:60ubuntu1) wird eingerichtet ...
Created symlink /etc/systemd/system/timers.target.wants/phpsessionclean.timer → /lib/systemd/system/phpsessionclean.timer.
Trigger für man-db (2.8.3-2) werden verarbeitet ...
php7.2-common (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/calendar.ini with new version

Creating config file /etc/php/7.2/mods-available/ctype.ini with new version

Creating config file /etc/php/7.2/mods-available/exif.ini with new version

Creating config file /etc/php/7.2/mods-available/fileinfo.ini with new version

Creating config file /etc/php/7.2/mods-available/ftp.ini with new version

Creating config file /etc/php/7.2/mods-available/gettext.ini with new version

Creating config file /etc/php/7.2/mods-available/iconv.ini with new version

Creating config file /etc/php/7.2/mods-available/pdo.ini with new version

Creating config file /etc/php/7.2/mods-available/phar.ini with new version

Creating config file /etc/php/7.2/mods-available/posix.ini with new version

Creating config file /etc/php/7.2/mods-available/shmop.ini with new version

Creating config file /etc/php/7.2/mods-available/sockets.ini with new version

Creating config file /etc/php/7.2/mods-available/sysvmsg.ini with new version

Creating config file /etc/php/7.2/mods-available/sysvsem.ini with new version

Creating config file /etc/php/7.2/mods-available/sysvshm.ini with new version

Creating config file /etc/php/7.2/mods-available/tokenizer.ini with new version
php7.2-readline (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/readline.ini with new version
php7.2-json (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/json.ini with new version
php7.2-opcache (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/opcache.ini with new version
php7.2-mysql (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/mysqlnd.ini with new version

Creating config file /etc/php/7.2/mods-available/mysqli.ini with new version

Creating config file /etc/php/7.2/mods-available/pdo_mysql.ini with new version
php7.2-cli (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...
update-alternatives: /usr/bin/php7.2 wird verwendet, um /usr/bin/php (php) im automatischen Modus bereitzustellen
update-alternatives: /usr/bin/phar7.2 wird verwendet, um /usr/bin/phar (phar) im automatischen Modus bereitzustellen
update-alternatives: /usr/bin/phar.phar7.2 wird verwendet, um /usr/bin/phar.phar (phar.phar) im automatischen Modus bereitzustellen

Creating config file /etc/php/7.2/cli/php.ini with new version
libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/apache2/php.ini with new version
Module mpm_event disabled.
Enabling module mpm_prefork.
apache2_switch_mpm Switch to prefork
apache2_invoke: Enable module php7.2
php-mysql (1:7.2+60ubuntu1) wird eingerichtet ...
libapache2-mod-php (1:7.2+60ubuntu1) wird eingerichtet ...
php7.2 (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...
php (1:7.2+60ubuntu1) wird eingerichtet ...
```

Die Installation von PHP erfolgt ohne Probleme.  

In den meisten Fällen möchten ich die Art und Weise ändern, 
in der Apache Dateien bereitstellt, wenn ein Verzeichnis angefordert wird. 
Wenn ein Benutzer momentan ein Verzeichnis vom Server anfordert, 
sucht Apache zunächst nach einer Datei namens `index.html`. 
Ich möchte, dass der Web-Server PHP-Dateien vor anderen Dateien mit anderen Endungen bevorzugt. 
Deshalb lasse ich Apache zuerst nach einer `index.php-Datei` suchen.

Ich gebe den Befehl `sudo gedit /etc/apache2/mods-enabled/dir.conf` ein, um die Datei 
`dir.conf` in einem Texteditor mit `root-Rechten` zu öffnen.

```
astrid@astrid-TravelMate-5760G:~$ sudo gedit /etc/apache2/mods-enabled/dir.conf
```

Die Datei sieht wie folgt aus:

```
<IfModule mod_dir.c>
	DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>
```

Ich verschieben die PHP-Indexdatei an die erste Position.

```
<IfModule mod_dir.c>
	DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```

Danach starte ich den Apache-Webserver neu, 
damit meine Änderungen übernommen werden.

```
astrid@astrid-TravelMate-5760G:~$ sudo systemctl restart apache2
```

Ich kann den Status des apache2-Dienstes mit dem Befehl `systemctl` prüfen:

```
astrid@astrid-TravelMate-5760G:~$ sudo systemctl status apache2
● apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           └─apache2-systemd.conf
   Active: active (running) since Fri 2018-10-12 15:27:43 CEST; 8s ago
  Process: 14549 ExecStop=/usr/sbin/apachectl stop (code=exited, status=0/SUCCES
  Process: 14554 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCC
 Main PID: 14558 (apache2)
    Tasks: 6 (limit: 4915)
   CGroup: /system.slice/apache2.service
           ├─14558 /usr/sbin/apache2 -k start
           ├─14559 /usr/sbin/apache2 -k start
           ├─14560 /usr/sbin/apache2 -k start
           ├─14561 /usr/sbin/apache2 -k start
           ├─14562 /usr/sbin/apache2 -k start
           └─14563 /usr/sbin/apache2 -k start

Okt 12 15:27:43 astrid-TravelMate-5760G systemd[1]: Starting The Apache HTTP Ser
Okt 12 15:27:43 astrid-TravelMate-5760G apachectl[14554]: AH00558: apache2: Coul
Okt 12 15:27:43 astrid-TravelMate-5760G systemd[1]: Started The Apache HTTP Serv
```

Ich drücken `Q`, um diese Statusausgabe zu beenden.  

Um die Funktionalität von PHP zu erweitern, haben ich die Möglichkeit, 
einige zusätzliche Module zu installieren. 
Um die verfügbaren Optionen für PHP-Module anzuzeigen, führe ich den Befehl 
`apt search php- | less` aus.

```
astrid@astrid-TravelMate-5760G:~$ apt search php- | less
```

Dieser Befehl zeigt mir die folgende Ausgabe an. Ich scrolle mit den 
Pfeiltasten auf und ab und drücken Sie `Q` zum Beenden.

Die Ergebnisse sind alle optionale Komponenten, die ich installieren kann. 
Ich kann mir eine kurze Beschreibung für jedes anzeigen lassen. Wie das geht zeige ich weiter unten.

```
Sortierung...
Volltextsuche...
bandwidthd/bionic 2.0.1+cvs20090917-10ubuntu1 amd64
  Verfolgt die Verwendung von TCP/IP und erstellt HTML-Dateien mit Graphen

bandwidthd-pgsql/bionic 2.0.1+cvs20090917-10ubuntu1 amd64
  Verfolgt die Verwendung von TCP/IP und erstellt HTML-Dateien mit Graphen

bluefish/bionic 2.2.10-1 amd64
  Fortschrittlicher GTK+-Texteditor für Software- und Webentwicklung

cacti/bionic,bionic 1.1.38+ds1-1 all
  Weboberfläche zur Visualisierung von Überwachungssystemen

debpear/bionic,bionic 0.5 all
  Baut und installiert PEAR-Pakete automatisch als Debian-Pakete

dia2code/bionic 0.8.3-4build1 amd64
  dia-UML Code-Generator

ganglia-webfrontend/bionic,bionic 3.6.1-3 all
  cluster monitoring toolkit - web front-end

golang-github-unknwon-cae-dev/bionic,bionic 0.0~git20160715.0.c6aac99-4 all
  PHP-like Compression and Archive Extensions in Go

haserl/bionic 0.9.35-2 amd64
  CGI scripting program for embedded environments

kdevelop-php/bionic 5.2.1-1ubuntu2 amd64
  PHP-Erweiterung für KDevelop

kdevelop-php-docs/bionic,bionic 5.2.1-1ubuntu2 all
  transitional package for kdevelop-php

kdevelop-php-docs-l10n/bionic,bionic 5.2.1-1ubuntu2 all
  transitional package for kdevelop-php-l10n

kdevelop-php-l10n/bionic,bionic 5.2.1-1ubuntu2 all
  localization files for KDevelop PHP plugin

libawl-php/bionic,bionic 0.59-1 all
  Andrews Web-Bibliotheken – PHP-Hilfsbibliotheken

libcode-tidyall-perl/bionic,bionic 0.67-1 all
  your all-in-one code tidier and validator

libjs-edit-area/bionic,bionic 0.8.2-1 all
  Freier Javascript-Quelltexteditor

libnet-libidn-perl/bionic,now 0.12.ds-2build4 amd64  [installiert]
  Perl-Anbindungen für GNU Libidn

libnusoap-php/bionic,bionic 0.9.5-3 all
  SOAP-Werkzeugsatz für PHP

libphp-adodb/bionic,bionic 5.20.9-1 all
  ADOdb is a PHP database abstraction layer library

libphp-embed/bionic,bionic 1:7.2+60ubuntu1 all
  HTML-embedded scripting language (Embedded SAPI library) (default)

libphp-jabber/bionic,bionic 0.4.3-5 all
  Object-oriented PHP interface for the Jabber/XMPP protocol

libphp-jpgraph/bionic,bionic 1.5.2-13 all
  Object oriented graph library for php

libphp-jpgraph-examples/bionic,bionic 1.5.2-13 all
  Object oriented graph library for php (examples)

libphp-magpierss/bionic,bionic 0.72-11 all
  provides an XML-based RSS parser in PHP

libphp-phpmailer/bionic,bionic 5.2.14+dfsg-2.3 all
  Voll funktionsfähige PHP-Klasse für E-Mail-Transfer

libphp-predis/bionic 0.8.3-1ubuntu1 amd64
  Flexible and feature-complete PHP client library for the Redis key-value store

libphp-serialization-perl/bionic,bionic 0.34-2 all
  Perl-Modul zur Manipulation serialisierter PHP-Datenstrukturen

libphp-simplepie/bionic,bionic 1.3.1+dfsg-3.1 all
  RSS and Atom feed parsing in PHP

libphp-snoopy/bionic,bionic 2.0.0-2 all
  PHP-Klasse, die einen Webbrowser simuliert

libphp-swiftmailer/bionic,bionic 5.4.2-1.1 all
  Übergangspaket

mlmmj-php-web/bionic,bionic 1.3.0-2 all
  web interface for mlmmj, written in php

mlmmj-php-web-admin/bionic,bionic 1.3.0-2 all
  administrative web interface for mlmmj, written in php

php-all-dev/bionic,bionic 1:60ubuntu1 all
  package depending on all supported PHP development packages

php-amqp/bionic 1.7.1-1build2 amd64
  AMQP extension for PHP

php-amqplib/bionic,bionic 2.7.0-1 all
  pure PHP implementation of the AMQP protocol

php-analog/bionic,bionic 1.0.7-2 all
  PHP micro logging package

php-apcu/bionic 5.1.9+4.0.11-1build1 amd64
  APC User Cache for PHP

php-apcu-bc/bionic 1.0.3-2ubuntu2 amd64
  APCu Backwards Compatibility Module

php-apigen-theme-bootstrap/bionic,bionic 1.1.3+dfsg-3 all
  Twitter Bootstrap theme for ApiGen

php-apigen-theme-default/bionic,bionic 1.0.2+dfsg-3 all
  Default theme for ApiGen

php-ast/bionic 0.1.6-1 amd64
  AST extension for PHP 7

php-auth-sasl/bionic,bionic 1.0.6-3 all
  Abstraktion von Antworten für verschiedene SASL-Mechanismen

php-bcmath/bionic,bionic 1:7.2+60ubuntu1 all
  Bcmath module for PHP [default]

php-bz2/bionic,bionic 1:7.2+60ubuntu1 all
  bzip2 module for PHP [default]

php-cache-integration-tests/bionic,bionic 0.16.0-2 all
  Integration tests for PSR-6 and PSR-16 cache implementations

php-cache-lite/bionic,bionic 1.7.16-2ubuntu1 all
  Fast and Safe little cache system

php-cache-tag-interop/bionic,bionic 1.0.0-1 all
  Framework interoperable interfaces for tags

php-cas/bionic,bionic 1.3.3-4 all
  Central Authentication Service client library in php

php-cassandra/bionic 1.3.0-1build1 amd64
  DataStax PHP Driver for Apache Cassandra

php-cgi/bionic,bionic 1:7.2+60ubuntu1 all
  server-side, HTML-embedded scripting language (CGI binary) (default)

php-cli/bionic,bionic 1:7.2+60ubuntu1 all
  command-line interpreter for the PHP scripting language (default)

php-cli-prompt/bionic,bionic 1.0.3+dfsg-1 all
  tiny helper prompting for user input

php-codecoverage/bionic,bionic 5.3.0+dfsg-1ubuntu2 all
  collection, processing, and rendering for code coverage

php-codesniffer/bionic,bionic 3.2.3-1 all
  PHP, CSS and JavaScript coding standard analyzer and checker

php-common/bionic,bionic,now 1:60ubuntu1 all  [Installiert,automatisch]
  Common files for PHP packages

php-composer-ca-bundle/bionic,bionic 1.1.0-1 all
  utility library to find a path to the system CA bundle

php-composer-semver/bionic,bionic 1.4.2-1 all
  utilities, version constraint parsing and validation

php-composer-spdx-licenses/bionic,bionic 1.3.0-1 all
  SPDX licenses list and validation library

php-console-commandline/bionic,bionic 1.2.1-1 all
  A full featured command line options and arguments parser

php-console-table/bionic,bionic 1.3.1-0.1 all
  Library that makes it easy to build console style tables

php-constant-time/bionic,bionic 2.2.0-1 all
  Constant-time Implementations of RFC 4648 Encoding (Base-64, Base-32, Base-16)

php-curl/bionic,bionic 1:7.2+60ubuntu1 all
  CURL module for PHP [default]

php-date/bionic,bionic 1.4.7-3 all
  Generic date/time handling class for PEAR

php-db/bionic,bionic 1.9.2-2ubuntu1 all
  Database Abstraction Layer

php-db-dataobject/bionic,bionic 1.11.5-1 all
  PHP PEAR module for object based SQL query building

php-deepcopy/bionic,bionic 1.7.0-1 all
  create deep copies (clones) of objects

php-dev/bionic,bionic 1:7.2+60ubuntu1 all
  Files for PHP module development (default)

php-directory-scanner/bionic,bionic 1.3.2-2 all
  recursive directory scanner and filter

php-doctrine-annotations/bionic,bionic 1.5.0really1.2.7-1 all
  Docblock Annotations Parser - Doctrine component

php-doctrine-bundle/bionic,bionic 1.8.1-1 all
  bundle library - Doctrine component

php-doctrine-cache/bionic,bionic 1.7.1-1 all
  cache library - Doctrine component

php-doctrine-cache-bundle/bionic,bionic 1.3.2-3 all
  cache bundle library - Doctrine component

php-doctrine-collections/bionic,bionic 1.5.0-1 all
  Collections Abstraction library - Doctrine component

php-doctrine-common/bionic,bionic 2.6.1-2 all
  common extensions for Doctrine

php-doctrine-data-fixtures/bionic,bionic 1.2.2-2 all
  Data Fixtures for all Doctrine Object Managers

php-doctrine-dbal/bionic,bionic 2.5.13-1 all
  database abstraction layer for Doctrine

php-doctrine-inflector/bionic,bionic 1.2.0-1 all
  string manipulations library - Doctrine component

php-doctrine-instantiator/bionic,bionic 1.0.5-3 all
  lightweight utility to instantiate objects in PHP

php-doctrine-lexer/bionic,bionic 1.0.1-4 all
  base lexer library - Doctrine component

php-doctrine-orm/bionic,bionic 2.5.14+dfsg-1 all
  tool for object-relational mapping

php-dompdf/bionic,bionic 0.6.2+dfsg-3 all
  HTML to PDF converter

php-ds/bionic 1.1.8-1build1 amd64
  PHP extension providing efficient data structures for PHP 7

php-elisp/bionic,bionic 1.13.5-3 all
  Emacs-Unterstützung für PHP-Dateien

php-email-validator/bionic,bionic 2.1.3-1 all
  A library for validating emails against several RFCs

php-enchant/bionic,bionic 1:7.2+60ubuntu1 all
  Enchant module for PHP [default]

php-enum/bionic,bionic 3.0.0-1 all
  Simple and fast implementation of enumerations with native PHP>=5.6

php-facedetect/bionic 1.1.0+git20170801-1build1 amd64
  Detect faces with PHP

php-fdomdocument/bionic,bionic 1.6.6-1 all
  extension to PHP's standard DOM

php-fig-link-util/bionic,bionic 1.0.0-2 all
  Common utility implementations for HTTP links

php-file-iterator/bionic,bionic 1.4.5-1 all
  FilterIterator implementation for PHP

php-finder-facade/bionic,bionic 1.2.2-2 all
  convenience wrapper for Symfony's Finder component

php-finder-facade-doc/bionic,bionic 1.2.2-2 all
  convenience wrapper for Symfony's Finder component - documentation

php-font-lib/bionic,bionic 0.3.1+dfsg-3 all
  read, parse, export and make subsets of different fonts

php-fpdf/bionic,bionic 3:1.8.1.dfsg-2 all
  PHP class to generate PDF files

php-fpm/bionic,bionic 1:7.2+60ubuntu1 all
  server-side, HTML-embedded scripting language (FPM-CGI binary) (default)

php-fshl/bionic,bionic 2.1.0-4 all
  Fast Syntax HighLighter

php-fxsl/bionic,bionic 1.1.1-3 all
  XSL wrapper and extension to XSLTProcessor

php-gd/bionic,bionic 1:7.2+60ubuntu1 all
  GD module for PHP [default]

php-gearman/bionic 2.0.3+1.1.2+-1build3 amd64
  PHP wrapper to libgearman

php-geoip/bionic 1.1.1-1build2 amd64
  GeoIP module for PHP

php-geos/bionic 1.0.0-2build2 amd64
  GEOS bindings for PHP

php-geshi/bionic,bionic 1.0.8.11-2.1 all
  Generische Syntaxhervorhebung

php-getid3/bionic,bionic 1.9.15+dfsg-1 all
  scripts to extract information from multimedia files

php-gettext/bionic,bionic 1.0.12-0.1 all
  transitional dummy package for php-php-gettext

php-gmagick/bionic 2.0.4~rc1+1.1.7~rc3-1build2 amd64
  Provides a wrapper to the GraphicsMagick library

php-gmp/bionic,bionic 1:7.2+60ubuntu1 all
  GMP module for PHP [default]

php-gnupg/bionic 1.4.0-1build2 amd64
  PHP wrapper around the gpgme library

php-guestfs/bionic-updates 1:1.36.13-1ubuntu3.2 amd64
  guest disk image management system - PHP bindings

php-guzzlehttp-promises/bionic,bionic 1.3.1-0ubuntu1 all
  Guzzle promises library

php-hamcrest/bionic,bionic 2.0.0-0ubuntu1 all
  This is the PHP port of Hamcrest Matchers

php-horde/bionic,bionic 5.2.17+debian0-1 all
  Horde Application Framework

php-horde-activesync/bionic,bionic 2.39.0-1ubuntu1 all
  ActiveSync server library

php-horde-alarm/bionic,bionic 2.2.10-1ubuntu1 all
  Horde Alarm Libraries

php-horde-ansel/bionic,bionic 3.0.8+debian0-1ubuntu1 all
  Photo management application

php-horde-argv/bionic,bionic 2.1.0-1ubuntu1 all
  Horde command-line argument parsing package

php-horde-auth/bionic,bionic 2.2.2-1ubuntu1 all
  Horde Authentication API

php-horde-autoloader/bionic,bionic 2.1.2-3ubuntu1 all
  Horde Autoloader

php-horde-browser/bionic,bionic 2.0.15-1 all
  Horde Browser API

php-horde-cache/bionic,bionic 2.5.5-1 all
  Horde Caching API

php-horde-cli/bionic,bionic 2.2.4-1 all
  Horde Command Line Interface API

php-horde-compress/bionic,bionic 2.2.1-1ubuntu1 all
  Horde Compression API

php-horde-compress-fast/bionic,bionic 1.1.1-3 all
  Fast Compression Library

php-horde-constraint/bionic,bionic 2.0.3-3 all
  Horde Constraint library

php-horde-content/bionic,bionic 2.0.6-1 all
  Tagging application

php-horde-controller/bionic,bionic 2.0.4-3ubuntu1 all
  Horde Controller libraries

php-horde-core/bionic,bionic 2.31.1+debian0-1ubuntu1 all
  Core Horde Framework library

php-horde-crypt/bionic,bionic 2.7.11-1ubuntu1 all
  Horde Cryptography API

php-horde-crypt-blowfish/bionic,bionic 1.1.2-1ubuntu1 all
  Blowfish Encryption Library

php-horde-css-parser/bionic,bionic 1.0.11-1ubuntu1 all
  Horde CSS Parser

php-horde-cssminify/bionic,bionic 1.0.4-1 all
  CSS Minification

php-horde-data/bionic,bionic 2.1.4-3ubuntu1 all
  Horde Data API

php-horde-date/bionic,bionic 2.4.1-1ubuntu1 all
  Horde Date package

php-horde-date-parser/bionic,bionic 2.0.6-1ubuntu1 all
  Horde Date Parser

php-horde-dav/bionic,bionic 1.1.4-1 all
  Horde library for WebDAV, CalDAV, CardDAV

php-horde-db/bionic,bionic 2.4.0-1ubuntu2 all
  Horde Database Libraries

php-horde-editor/bionic,bionic 2.0.4+debian0-8 all
  Horde Editor API

php-horde-elasticsearch/bionic,bionic 1.0.4-1 all
  Horde ElasticSearch client

php-horde-exception/bionic,bionic 2.0.8-2ubuntu1 all
  Horde Exception Handler

php-horde-feed/bionic,bionic 2.0.4-3ubuntu1 all
  Horde Feed libraries

php-horde-form/bionic,bionic 2.0.18-1 all
  Horde Form API

php-horde-gollem/bionic,bionic 3.0.12-1 all
  Web-based file manager

php-horde-group/bionic,bionic 2.1.1-2 all
  Horde User Groups System

php-horde-groupware/bionic,bionic 5.2.22-1 all
  Horde Groupware

php-horde-hashtable/bionic,bionic 1.2.6-1 all
  Horde Hash Table Interface

php-horde-history/bionic,bionic 2.3.6-3ubuntu1 all
  API for tracking the history of an object

php-horde-http/bionic,bionic 2.1.7-1 all
  Horde HTTP libraries

php-horde-icalendar/bionic,bionic 2.1.7-1 all
  iCalendar API

php-horde-idna/bionic,bionic 1.1.1-1 all
  IDNA backend normalization package

php-horde-image/bionic,bionic 2.5.2-1 all
  Horde Image API

php-horde-imap-client/bionic,bionic 2.29.15-1 all
  Horde IMAP Client

php-horde-imp/bionic,bionic 6.2.21-1ubuntu1 all
  A web based webmail system

php-horde-imsp/bionic,bionic 2.0.10-1 all
  IMSP API

php-horde-ingo/bionic,bionic 3.2.16-1ubuntu1 all
  An email filter rules manager

php-horde-injector/bionic,bionic 2.0.5-3ubuntu1 all
  Horde dependency injection container

php-horde-itip/bionic,bionic 2.1.2-2ubuntu1 all
  iTip invitation response handling

php-horde-javascriptminify/bionic,bionic 1.1.5-1 all
  Javascript Minification

php-horde-javascriptminify-jsmin/bionic,bionic 1.0.2-3ubuntu1 all
  Horde Javascript Minifier - Jsmin PHP Driver

php-horde-kolab-format/bionic,bionic 2.0.9-1ubuntu1 all
  A package for reading/writing Kolab data formats

php-horde-kolab-server/bionic,bionic 2.0.5-3 all
  A package for manipulating the Kolab user database

php-horde-kolab-session/bionic,bionic 2.0.3-3ubuntu2 all
  A package managing an active Kolab session

php-horde-kolab-storage/bionic,bionic 2.2.3-1ubuntu1 all
  A package for handling Kolab data stored on an IMAP server

php-horde-kronolith/bionic,bionic 4.2.23-1ubuntu1 all
  A web based calendar

php-horde-ldap/bionic,bionic 2.4.0-1ubuntu1 all
  Horde LDAP libraries

php-horde-listheaders/bionic,bionic 1.2.5-1ubuntu1 all
  Horde List Headers Parsing Library

php-horde-lock/bionic,bionic 2.1.4-1 all
  Horde Resource Locking System

php-horde-log/bionic,bionic 2.3.0-1ubuntu1 all
  Horde Logging library

php-horde-logintasks/bionic,bionic 2.0.7-2ubuntu1 all
  Horde Login Tasks System

php-horde-lz4/bionic 1.0.10-2ubuntu1 amd64
  Horde LZ4 Compression Extension

php-horde-mail/bionic,bionic 2.6.4-1ubuntu1 all
  Horde Mail Library

php-horde-mail-autoconfig/bionic,bionic 1.0.3-2 all
  Horde Mail Autoconfiguration

php-horde-mapi/bionic,bionic 1.0.8-2ubuntu2 all
  MAPI utility library

php-horde-memcache/bionic,bionic 2.1.1-1 all
  Horde Memcache API

php-horde-mime/bionic,bionic 2.10.3-1ubuntu1 all
  Horde MIME Library

php-horde-mime-viewer/bionic,bionic 2.2.2-1 all
  Horde MIME Viewer Library

php-horde-mnemo/bionic,bionic 4.2.14-1ubuntu1 all
  A web based notes manager

php-horde-mongo/bionic,bionic 1.1.0-1 all
  Horde Mongo Configuration

php-horde-nag/bionic,bionic 4.2.17-1ubuntu1 all
  A web based task list manager

php-horde-nls/bionic,bionic 2.2.1-1 all
  Native Language Support (NLS)

php-horde-notification/bionic,bionic 2.0.4-3ubuntu1 all
  Horde Notification System

php-horde-oauth/bionic,bionic 2.0.4-1 all
  Horde OAuth client/server

php-horde-openxchange/bionic,bionic 1.0.1-1 all
  Open-Xchange Connector

php-horde-pack/bionic,bionic 1.0.7-1 all
  Horde Pack Utility

php-horde-passwd/bionic,bionic 5.0.7-1ubuntu1 all
  Horde password changing application

php-horde-pdf/bionic,bionic 2.0.7-3ubuntu1 all
  Horde PDF library

php-horde-perms/bionic,bionic 2.1.7-2ubuntu1 all
  Horde Permissions System

php-horde-prefs/bionic,bionic 2.9.0-1ubuntu1 all
  Horde Preferences API

php-horde-queue/bionic,bionic 1.1.5-1 all
  Horde Queue

php-horde-rdo/bionic,bionic 2.1.0-1 all
  Rampage Data Objects

php-horde-role/bionic,bionic 1.0.1-12 all
  PEAR installer role used to install Horde components

php-horde-routes/bionic,bionic 2.0.5-3ubuntu1 all
  Horde Routes URL mapping system

php-horde-rpc/bionic,bionic 2.1.8-1 all
  Horde RPC API

php-horde-scheduler/bionic,bionic 2.0.3-1 all
  Horde Scheduler System

php-horde-scribe/bionic,bionic 2.0.3-1 all
  Scribe

php-horde-secret/bionic,bionic 2.0.6-3ubuntu1 all
  Secret Encryption API

php-horde-serialize/bionic,bionic 2.0.5-3ubuntu1 all
  Data Encapulation API

php-horde-service-facebook/bionic,bionic 2.0.10-1 all
  Facebook-Client für Horde

php-horde-service-gravatar/bionic,bionic 1.0.1-3ubuntu1 all
  API accessor for gravatar.com

php-horde-service-twitter/bionic,bionic 2.1.6-1 all
  Horde Twitter client

php-horde-service-urlshortener/bionic,bionic 2.0.3-1 all
  Horde_Service_UrlShortener Class

php-horde-service-weather/bionic,bionic 2.5.4-1ubuntu1 all
  Horde Weather Provider

php-horde-sesha/bionic,bionic 1.0.0~rc3-1 all
  A simple Inventory App for Horde

php-horde-sessionhandler/bionic,bionic 2.2.9-1ubuntu1 all
  Horde Session Handler API

php-horde-share/bionic,bionic 2.2.0-1ubuntu1 all
  Horde Shared Permissions System

php-horde-smtp/bionic,bionic 1.9.5-1ubuntu1 all
  Horde SMTP Client

php-horde-socket-client/bionic,bionic 2.1.1-3 all
  Horde Socket Client

php-horde-spellchecker/bionic,bionic 2.1.3-3ubuntu1 all
  Spellcheck API

php-horde-stream/bionic,bionic 1.6.3-3 all
  Horde stream handler

php-horde-stream-filter/bionic,bionic 2.0.4-3 all
  Horde Stream filters

php-horde-stream-wrapper/bionic,bionic 2.1.4-0ubuntu2 all
  PHP stream wrappers library

php-horde-support/bionic,bionic 2.2.0-1ubuntu1 all
  Horde support package

php-horde-syncml/bionic,bionic 2.0.7-2 all
  Horde_SyncMl provides an API for processing SyncML requests

php-horde-template/bionic,bionic 2.0.3-3 all
  Horde Template System

php-horde-test/bionic,bionic 2.6.3+debian0-1ubuntu2 all
  Horde testing base classes

php-horde-text-diff/bionic,bionic 2.2.0-1ubuntu1 all
  Engine for performing and rendering text diffs

php-horde-text-filter/bionic,bionic 2.3.5-1ubuntu1 all
  Horde Text Filter API

php-horde-text-filter-jsmin/bionic,bionic 1.0.2-3ubuntu1 all
  Horde Text Filter - Jsmin PHP Driver

php-horde-text-flowed/bionic,bionic 2.0.3-3ubuntu1 all
  Horde API for flowed text as per RFC 3676

php-horde-thrift/bionic,bionic 2.0.3-1 all
  Thrift

php-horde-timeobjects/bionic,bionic 2.1.4-1 all
  Horde timeobjects application

php-horde-timezone/bionic,bionic 1.1.0-1 all
  Timezone library

php-horde-token/bionic,bionic 2.0.9-2 all
  Horde Token API

php-horde-translation/bionic,bionic 2.2.2-1ubuntu1 all
  Horde translation library

php-horde-trean/bionic,bionic 1.1.9-1 all
  Web-based bookmarks application

php-horde-tree/bionic,bionic 2.0.5-1 all
  Horde Tree API

php-horde-turba/bionic,bionic 4.2.21-1ubuntu1 all
  A web based address book

php-horde-url/bionic,bionic 2.2.6-1ubuntu1 all
  Horde Url class

php-horde-util/bionic,bionic 2.5.8-1ubuntu1 all
  Horde Utility Libraries

php-horde-vfs/bionic,bionic 2.4.0-1ubuntu1 all
  Virtual File System API

php-horde-view/bionic,bionic 2.0.6-3ubuntu1 all
  Horde View API

php-horde-webmail/bionic,bionic 5.2.22-1 all
  Horde Groupware Webmail Edition

php-horde-whups/bionic,bionic 3.0.12-1 all
  Ticket-tracking application

php-horde-wicked/bionic,bionic 2.0.8-1ubuntu1 all
  Wiki application

php-horde-xml-element/bionic,bionic 2.0.4-3ubuntu1 all
  Horde Xml Element object

php-horde-xml-wbxml/bionic,bionic 2.0.3-3ubuntu1 all
  Horde_Xml_Wbxml provides an API for encoding and decoding WBXML documents used in SyncML and other wireless applications

php-html-safe/bionic,bionic 0.10.1-5 all
  strip down all potentially dangerous content within HTML

php-htmlawed/bionic,bionic 1.1.20-1 all
  htmLawed PHP code to purify & filter HTML

php-htmlpurifier/bionic,bionic 4.7.0-2 all
  Standards-compliant HTML filter

php-http/bionic 3.1.0+2.6.0-4build8 amd64
  PECL HTTP module for PHP Extended HTTP Support

php-http-request/bionic,bionic 1.4.4-5 all
  Provides an easy way to perform HTTP requests

php-http-request2/bionic,bionic 2.3.0-1ubuntu1 all
  Provides an easy way to perform HTTP requests

php-http-webdav-server/bionic,bionic 1.0.0RC8-1 all
  WebDAV Server Baseclass

php-icinga/bionic,bionic 2.4.1-1 all
  PHP library to communicate with and use Icinga

php-igbinary/bionic 2.0.5-1build1 amd64
  igbinary PHP serializer

php-image-text/bionic,bionic 0.7.0-2 all
  Image_Text - Advanced text maipulations in images

php-imagick/bionic 3.4.3~rc2-2ubuntu4 amd64
  Wrapper für die ImageMagick-Bibliothek

php-imap/bionic,bionic 1:7.2+60ubuntu1 all
  IMAP module for PHP [default]

php-interbase/bionic,bionic 1:7.2+60ubuntu1 all
  Interbase module for PHP [default]

php-intl/bionic,bionic 1:7.2+60ubuntu1 all
  Internationalisation module for PHP [default]

php-invoker/bionic,bionic 1.1.4-3 all
  Utility class for invoking callables with a timeout

php-jmespath/bionic,bionic 2.3.0-2ubuntu1 all
  Declaratively specify how to extract elements from a JSON document

php-json/bionic,bionic 1:7.2+60ubuntu1 all
  JSON module for PHP [default]

php-json-schema/bionic,bionic 5.2.6-1 all
  implementation of JSON schema

php-kdyby-events/bionic,bionic 2.4.0-3 all
  Events for Nette Framework

php-klogger/bionic,bionic 1.2.1-2 all
  simple logging class

php-ldap/bionic,bionic 1:7.2+60ubuntu1 all
  LDAP module for PHP [default]

php-letodms-core/bionic,bionic 3.4.2-1 all
  Document management system

php-letodms-lucene/bionic,bionic 1.1.1-2 all
  Document management system - Fulltext search

php-libsodium/bionic 1.0.6-1build3 amd64
  PHP wrapper for the Sodium cryptographic library

php-libvirt-php/bionic 0.5.4-1 amd64
  libvirt bindings for PHP

php-log/bionic,bionic 1.12.9-2 all
  Logging Framework

php-luasandbox/bionic 3.0.1-1 amd64
  PHP extension that provides a sandboxed Lua environment

php-mail/bionic,bionic 1.3.0-1 all
  Klasse mit mehreren Schnittstellen zum Versenden von E-Mails

php-mail-mime/bionic,bionic 1.10.2-0.1 all
  PHP-PEAR-Modul zur Erzeugung von MIME-Nachrichten

php-mailparse/bionic 3.0.2+2.1.6-12-gae1ef14-1build2 amd64
  Email message manipulation for PHP

php-mapi/bionic 8.5.5-0ubuntu1 amd64
  Complete and feature rich groupware solution - PHP MAPI bindings

php-markdown/bionic,bionic 1.6.0-2 all
  PHP library for rendering Markdown data

php-mbstring/bionic,bionic 1:7.2+60ubuntu1 all
  MBSTRING module for PHP [default]

php-mdb2/bionic,bionic 2.5.0b5-2 all
  database abstraction layer

php-mdb2-driver-mysql/bionic,bionic 1.5.0b4-2 all
  mysql MDB2 driver

php-mdb2-driver-pgsql/bionic,bionic 1.5.0b4-2 all
  pgsql MDB2 driver

php-memcache/bionic 3.0.9~20160311.4991c2f-5build2 amd64
  memcache extension module for PHP

php-memcached/bionic 3.0.1+2.2.0-1build2 amd64
  memcached extension module for PHP, uses libmemcached

php-mf2/bionic,bionic 0.3.0-0.1 all
  Microformats2 is the simplest way to markup structured information in HTML

php-mime-type/bionic,bionic 1.3.1-1build1 all
  Utility class for dealing with MIME types

php-mockery/bionic,bionic 1.0-0ubuntu1 all
  mock object framework for PHPUnit and other testing framework

php-mockery-doc/bionic,bionic 1.0-0ubuntu1 all
  mock object framework for PHPUnit - documentation

php-mongodb/bionic 1.3.4-1build1 amd64
  MongoDB driver for PHP

php-monolog/bionic,bionic 1.23.0-1ubuntu1 all
  send logs to various destination and web services

php-msgpack/bionic 2.0.2+0.5.7-2build1 amd64
  PHP extension for interfacing with MessagePack

php-mysql/bionic,bionic,now 1:7.2+60ubuntu1 all  [installiert]
  MySQL module for PHP [default]

php-mythtv/bionic,bionic 2:29.1+fixes.20180414.329c235-0ubuntu3 all
  PHP-Anbindungen für MythTV

php-net-dime/bionic,bionic 1.0.2-3 all
  The Net_DIME package implements DIME encoding and decoding

php-net-dns2/bionic,bionic 1.4.1-2 all
  PHP5 Resolver library used to communicate with a DNS server

php-net-ftp/bionic,bionic 1:1.4.0-2 all
  Net_FTP provides an OO interface to the PHP FTP functions plus some additions

php-net-idna2/bionic,bionic 0.1.1-1 all
  PHP Pear module for handling international domain names

php-net-imap/bionic,bionic 1:1.1.3-2 all
  Provides an implementation of the IMAP protocol

php-net-ipv6/bionic,bionic 1.3.0b3-1 all
  Check and validate IPv6 addresses

php-net-ldap2/bionic,bionic 2.2.0-3ubuntu1 all
  Object oriented interface for searching and manipulating LDAP-entries

php-net-ldap3/bionic,bionic 1.0.4-1 all
  Object oriented interface for searching and manipulating LDAP entries

php-net-nntp/bionic,bionic 1.5.0-2 all
  NNTP implementation

php-net-publicsuffix/bionic,bionic 0.2-1 all
  PHP module for detecting registered domains and public suffixes

php-net-sieve/bionic,bionic 1.4.1-1 all
  Handles talking to a sieve server

php-net-smtp/bionic,bionic 1.8.0-1 all
  PHP-PEAR-Modul, implementiert das SMTP-Protokoll

php-net-socket/bionic,bionic 1.0.14-2 all
  Network Socket Interface

php-net-url/bionic,bionic 1.0.15-4 all
  Easy parsing of Urls

php-net-url2/bionic,bionic 2.2.1-0.1 all
  Class for parsing and handling URL

php-net-whois/bionic,bionic 1.0.5-3.1 all
  PHP-PEAR-Modul zum Abfragen von whois-Diensten

php-nette/bionic,bionic 2.4-20160731-1 all
  Nette Framework

php-nrk-predis/bionic 1.0.0-1 amd64
  Flexible and feature-complete PHP client library for the Redis key-value store

php-numbers-words/bionic,bionic 0.18.1-2ubuntu1 all
  PEAR module providing methods for spelling numerals in words

php-oauth/bionic 2.0.2+1.2.3-1build2 amd64
  OAuth 1.0 consumer and provider extension

php-odbc/bionic,bionic 1:7.2+60ubuntu1 all
  ODBC module for PHP [default]

php-parser/bionic,bionic 3.1.4-1 all
  convert PHP code into abstract syntax tree

php-patchwork-utf8/bionic,bionic 1.3.1-1 all
  UTF-8 strings handling for PHP

php-pclzip/bionic,bionic 2.8.2-4 all
  ZIP archive manager class for PHP

php-pear/bionic,bionic 1:1.10.5+submodules+notgz-1ubuntu1 all
  PEAR Base System

php-pecl-http/bionic,bionic 3.1.0+2.6.0-4build8 all
  pecl_http module for PHP Extended HTTP Support [dummy]

php-pecl-http-dev/bionic,bionic 3.1.0+2.6.0-4build8 all
  pecl_http module for PHP Extended HTTP Support [dummy]

php-pgsql/bionic,bionic 1:7.2+60ubuntu1 all
  PostgreSQL module for PHP [default]

php-phar-io-manifest/bionic,bionic 1.0.1-2 all
  reading phar.io manifest information from a PHP Archive (Phar)

php-phar-io-version/bionic,bionic 1.0.1-1 all
  handling version information and constraint

php-php-gettext/bionic,bionic 1.0.12-0.1 all
  Liest gettext-MO-Dateien direkt und benötigt dafür nur PHP

php-phpdbg/bionic,bionic 1:7.2+60ubuntu1 all
  server-side, HTML-embedded scripting language (PHPDBG binary) (default)

php-phpdocumentor-reflection-common/bionic,bionic 1.0.1-1 all
  Common reflection classes - phpDocumentor component

php-phpdocumentor-reflection-docblock/bionic,bionic 4.2.0-2 all
  DocBlock parser - phpDocumentor component

php-phpdocumentor-type-resolver/bionic,bionic 0.4.0-2 all
  TypeResolver and FqsenResolver - phpDocumentor component

php-phpseclib/bionic,bionic 2.0.9-1 all
  implementations of an arbitrary-precision integer arithmetic library

php-phpspec-prophecy/bionic,bionic 1.7.3-1 all
  object mocking framework - phpspec component

php-pimple/bionic,bionic 3.0.2-2ubuntu1 all
  simple dependency injection container -- class

php-pinba/bionic 1.1.0-4build1 amd64
  Pinba module for PHP

php-propro/bionic 2.0.1+1.0.2-1build2 amd64
  propro module for PHP

php-propro-dev/bionic,bionic 2.0.1+1.0.2-1build2 all
  propro module for PHP development headers [dummy]

php-proxy-manager/bionic,bionic 2.1.1really2.0.4-1 all
  library providing utilities to operate with Object Proxies

php-ps/bionic 1.4.1-1build1 amd64
  ps module for PHP

php-pspell/bionic,bionic 1:7.2+60ubuntu1 all
  pspell module for PHP [default]

php-psr-cache/bionic,bionic 1.0.1-1 all
  Common interface for caching libraries

php-psr-container/bionic,bionic 1.0.0-1 all
  Common Container Interface (PHP FIG PSR-11)

php-psr-http-message/bionic,bionic 1.0.1-1 all
  Common interface for HTTP messages

php-psr-link/bionic,bionic 1.0.0-1 all
  Common interfaces for HTTP links

php-psr-log/bionic,bionic 1.0.2-1 all
  common interface for logging libraries

php-psr-simple-cache/bionic,bionic 1.0.0-1 all
  Common interfaces for simple caching

php-radius/bionic 1.4.0~b1-6build2 amd64
  radius client library for PHP

php-random-compat/bionic,bionic 2.0.11-1 all
  PHP 5.x polyfill for random_bytes() and random_int() from PHP 7

php-raphf/bionic 2.0.0+1.1.2-2build2 amd64
  raphf module for PHP

php-raphf-dev/bionic,bionic 2.0.0+1.1.2-2build2 all
  raphf module for PHP development headers [dummy]

php-react-promise/bionic,bionic 2.4.1-1ubuntu1 all
  lightweight implementation of CommonJS Promises/A for PHP

php-readline/bionic,bionic 1:7.2+60ubuntu1 all
  readline module for PHP [default]

php-recode/bionic,bionic 1:7.2+60ubuntu1 all
  recode module for PHP [default]

php-redis/bionic 3.1.6-1build1 amd64
  PHP extension for interfacing with Redis

php-remctl/bionic 3.13-1+deb9u1 amd64
  PECL module for Kerberos-authenticated command execution

php-rrd/bionic 2.0.1+1.1.3-4build1 amd64
  PHP-Anbindungen für das RRDtool-System.

php-sabre-dav/bionic,bionic 1.8.12-3ubuntu2 all
  WebDAV Framework for PHP

php-sabre-vobject/bionic,bionic 2.1.7-4 all
  library to parse and manipulate iCalendar and vCard objects

php-sass/bionic 0.5.10-3build1 amd64
  PHP bindings to libsass - fast, native Sass parsing in PHP

php-seclib/bionic,bionic 1.0.9-1 all
  implementations of an arbitrary-precision integer arithmetic library

php-services-json/bionic,bionic 1.0.3-1build1 all
  PHP-Implementierung von json_encode/decode

php-services-weather/bionic,bionic 1.4.7-4 all
  This class acts as an interface to various online weather-services

php-smbclient/bionic 0.8.0-3build2 amd64
  PHP wrapper for libsmbclient

php-snmp/bionic,bionic 1:7.2+60ubuntu1 all
  SNMP module for PHP [default]

php-soap/bionic,bionic 1:7.2+60ubuntu1 all
  SOAP module for PHP [default]

php-solr/bionic 2.4.0-5build1 amd64
  PHP extension for communicating with Apache Solr server

php-sql-formatter/bionic,bionic 1.2.17-2 all
  a PHP SQL highlighting library

php-sqlite3/bionic,bionic 1:7.2+60ubuntu1 all
  SQLite3 module for PHP [default]

php-ssh2/bionic 1.1.2+0.13-1build1 amd64
  Bindings for the libssh2 library

php-stomp/bionic 2.0.1+1.0.9-4 amd64
  Streaming Text Oriented Messaging Protocol (STOMP) client module for PHP

php-swiftmailer/bionic,bionic 5.4.2-1.1 all
  Swiftmailer, free feature-rich PHP mailer

php-sybase/bionic,bionic 1:7.2+60ubuntu1 all
  Sybase module for PHP [default]

php-symfony/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  set of reusable components and framework for web projects

php-symfony-asset/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  manage asset URLs

php-symfony-browser-kit/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  simulate the behavior of a web browser

php-symfony-cache/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  Symfony Cache component with PSR-6, PSR-16, and tags

php-symfony-class-loader/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  load PHP classes automatically

php-symfony-config/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  load configurations from different data sources

php-symfony-console/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  run tasks from the command line

php-symfony-css-selector/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  convert CSS selectors to XPath expressions

php-symfony-debug/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  tools to make debugging of PHP code easier

php-symfony-debug-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  debugging tools for the Symfony framework

php-symfony-dependency-injection/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  standardize and centralize construction of objects

php-symfony-doctrine-bridge/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  integration for Doctrine with Symfony Components

php-symfony-dom-crawler/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  ease DOM navigation for HTML and XML documents

php-symfony-dotenv/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  .env files parser to make environment variables accessible

php-symfony-event-dispatcher/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  dispatch events and listen to them

php-symfony-expression-language/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  compile and evaluate expressions

php-symfony-filesystem/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  basic filesystem utilities

php-symfony-finder/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  find files and directories

php-symfony-form/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  create HTML forms and process request data

php-symfony-framework-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  basic, robust and flexible MVC framework

php-symfony-http-foundation/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  object-oriented layer for the HTTP specification

php-symfony-http-kernel/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  building blocks for flexible and fast HTTP-based frameworks

php-symfony-inflector/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  words conversion between their singular and plural forms

php-symfony-intl/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  limited replacement layer for the PHP extension intl

php-symfony-ldap/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  abstraction layer for the PHP LDAP module

php-symfony-lock/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  creates and manages locks

php-symfony-monolog-bridge/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  integration for Monolog with Symfony Components

php-symfony-options-resolver/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  configure objects with option arrays

php-symfony-phpunit-bridge/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  integration for PHPUnit with Symfony Components

php-symfony-polyfill/bionic,bionic 1.6.0-2 all
  Symfony polyfills backporting features to lower PHP versions

php-symfony-polyfill-apcu/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting apcu_* functions to lower PHP versions

php-symfony-polyfill-iconv/bionic,bionic 1.6.0-2 all
  Symfony polyfill for the Iconv extension

php-symfony-polyfill-intl-grapheme/bionic,bionic 1.6.0-2 all
  Symfony polyfill for intl's grapheme_* functions

php-symfony-polyfill-intl-icu/bionic,bionic 1.6.0-2 all
  Symfony polyfill for intl's ICU-related data and classes

php-symfony-polyfill-intl-normalizer/bionic,bionic 1.6.0-2 all
  Symfony polyfill for intl's Normalizer class and related functions

php-symfony-polyfill-mbstring/bionic,bionic 1.6.0-2 all
  Symfony polyfill for the Mbstring extension

php-symfony-polyfill-php54/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 5.4+ features to lower PHP versions

php-symfony-polyfill-php55/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 5.5+ features to lower PHP versions

php-symfony-polyfill-php56/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 5.6+ features to lower PHP versions

php-symfony-polyfill-php70/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 7.0+ features to lower PHP versions

php-symfony-polyfill-php71/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 7.1+ features to lower PHP versions

php-symfony-polyfill-php72/bionic,bionic 1.6.0-2 all
  Symfony polyfill backporting some PHP 7.2+ features to lower PHP versions

php-symfony-polyfill-util/bionic,bionic 1.6.0-2 all
  Symfony utilities for portability of PHP codes

php-symfony-polyfill-xml/bionic,bionic 1.6.0-2 all
  Symfony polyfill for xml's utf8_encode and utf8_decode functions

php-symfony-process/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  execute commands in sub-processes

php-symfony-property-access/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  read from and write to an object or array

php-symfony-property-info/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  extract information about properties of PHP classes

php-symfony-proxy-manager-bridge/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  integration for ProxyManager with Symfony Components

php-symfony-routing/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  associate a request with code that generates a response

php-symfony-security/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  infrastructure for sophisticated authorization systems

php-symfony-security-acl/bionic,bionic 3.0.1-1 all
  Symfony Security Component - ACL (Access Control List)

php-symfony-security-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  configurable security system for the Symfony framework

php-symfony-security-core/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  infrastructure for authorization systems - common features

php-symfony-security-csrf/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  infrastructure for authorization systems - CSRF protection

php-symfony-security-guard/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  infrastructure for authorization systems - Guard features

php-symfony-security-http/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  infrastructure for authorization systems - HTTP integration

php-symfony-serializer/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  convert PHP objects into specific formats and vice versa

php-symfony-stopwatch/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  profile PHP code

php-symfony-templating/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  tools needed to build a template system

php-symfony-translation/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  tools to internationalize an application

php-symfony-twig-bridge/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  integration for Twig with Symfony Components

php-symfony-twig-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  configurable integration of Twig with the Symfony framework

php-symfony-validator/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  tools to validate classes

php-symfony-var-dumper/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  Symfony mechanism for exploring and dumping PHP variables

php-symfony-web-link/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  manage links between resources

php-symfony-web-profiler-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  collect requests information for analysis and debugging

php-symfony-web-server-bundle/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  provide commands for applications using the PHP built-in web server

php-symfony-workflow/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  manage a workflow or finite state machine

php-symfony-yaml/bionic-updates,bionic-updates,bionic-security,bionic-security 3.4.6+dfsg-1ubuntu0.1 all
  convert YAML to PHP arrays and the other way around

php-tcpdf/bionic,bionic 6.2.13+dfsg-1ubuntu1 all
  PHP-Klasse zum Erzeugen von PDF-Dateien im laufenden Betrieb

php-text-captcha/bionic,bionic 1.0.2-4ubuntu1 all
  Generation of CAPTCHAs

php-text-figlet/bionic,bionic 1.0.2-4 all
  Engine for use FIGlet fonts to rendering text

php-text-languagedetect/bionic,bionic 0.3.0-2 all
  Language detection class

php-text-password/bionic,bionic 1.2.1-2 all
  Creating passwords with PHP

php-text-template/bionic,bionic 1.2.1-2 all
  Simple template engine

php-text-wiki/bionic,bionic 1.2.1-3 all
  transform Wiki and BBCode markup into XHTML, LaTeX or plain text markup

php-tideways/bionic 4.0.7-1build2 amd64
  Tideways PHP Profiler Extension

php-tidy/bionic,bionic 1:7.2+60ubuntu1 all
  tidy module for PHP [default]

php-timer/bionic,bionic 1.0.9-1 all
  Utility class for timing

php-token-stream/bionic,bionic 2.0.2-1ubuntu2 all
  Wrapper around PHP's tokenizer extension

php-tokenizer/bionic,bionic 1.1.0-1 all
  tokenized PHP source to XML converter

php-tokenreflection/bionic,bionic 1.4.0-3 all
  PHP reflection replacement

php-twig/bionic,bionic 2.4.6-1 all
  Flexible, fast, and secure template engine for PHP

php-twig-doc/bionic,bionic 2.4.6-1 all
  Twig template engine documentation

php-uploadprogress/bionic 1.0.3.1-4-g95d8a0f-4build2 amd64
  file upload progress tracking extension for PHP

php-uuid/bionic 1.0.4-4build2 amd64
  PHP UUID extension

php-validate/bionic,bionic 0.8.5-4.1 all
  validation class

php-webmozart-assert/bionic,bionic 1.2.0-2 all
  Assertions to validate method input/output with nice error messages

php-wikidiff2/bionic 1.5.1-5 amd64
  Externe Vergleichs-Engine für MediaWiki

php-xajax/bionic,bionic 0.5-2 all
  A library to develop Ajax applications

php-xdebug/bionic 2.6.0-0ubuntu1 amd64
  Xdebug Module for PHP

php-xml/bionic,bionic 1:7.2+60ubuntu1 all
  DOM, SimpleXML, WDDX, XML, and XSL module for PHP [default]

php-xml-htmlsax3/bionic,bionic 3.0.0+really3.0.0-3 all
  SAX-Parser für HTML und andere schlecht geformte XML-Dokumente

php-xml-rpc2/bionic,bionic 1.1.3-0.1 all
  PHP XML-RPC client/server library

php-xml-svg/bionic,bionic 1.1.0-2 all
  XML_SVG API

php-xmlrpc/bionic,bionic 1:7.2+60ubuntu1 all
  XMLRPC-EPI module for PHP [default]

php-yac/bionic 2.0.1+0.9.2-1build2 amd64
  YAC (Yet Another Cache) for PHP

php-yaml/bionic 2.0.0+1.3.0-2build2 amd64
  YAML-1.1 parser and emitter for PHP

php-zend-code/bionic,bionic 3.2.0really3.1.0-1 all
  Zend Framework - Code component

php-zend-db/bionic,bionic 2.8.1-1 all
  Zend Framework - Db component

php-zend-eventmanager/bionic,bionic 3.2.0-1 all
  Zend Framework - EventManager component

php-zend-hydrator/bionic,bionic 2.2.2-1 all
  Zend Framework - Hydrator component

php-zend-stdlib/bionic,bionic 3.1.0-1 all
  Zend Framework - Stdlib component

php-zeroc-ice/bionic 3.7.0-5 amd64
  PHP extension for Ice

php-zeta-base/bionic,bionic 1.9-3ubuntu1 all
  Zeta Components - Base package

php-zeta-console-tools/bionic,bionic 1.7-3ubuntu1 all
  Zeta Components - ConsoleTools package

php-zeta-unit-test/bionic,bionic 1.0.2-3ubuntu2 all
  Zeta Components - UnitTest package

php-zip/bionic,bionic 1:7.2+60ubuntu1 all
  Zip module for PHP [default]

php-zmq/bionic 1.1.3-5build2 amd64
  ZeroMQ messaging bindings for PHP

php7.1-mapi/bionic,bionic 8.5.5-0ubuntu1 all
  transitional package for the rename of php7.1-mapi to php-mapi

phpunit-recursion-context/bionic,bionic 3.0.0-2 all
  PHP-Variablen rekursiv verarbeiten - PHPUnit-Komponente

pkg-php-tools/bionic,bionic 1.35ubuntu1 all
  various packaging tools and scripts for PHP packages

prayer/bionic 1.3.5-dfsg1-4build1 amd64
  Eigenständiger, IMAP-basierter Webmail-Server

prayer-accountd/bionic 1.3.5-dfsg1-4build1 amd64
  account management daemon for Prayer

prayer-templates-dev/bionic 1.3.5-dfsg1-4build1 amd64
  tools for compiling Prayer templates

prayer-templates-src/bionic,bionic 1.3.5-dfsg1-4build1 all
  templates for customizing Prayer Webmail

python-adodb/bionic,bionic 2.10-2 all
  Datenbankabstraktionsbibliothek für Python

srg/bionic 1.3.6-2ubuntu1 amd64
  Schnelle, flexible, detaillierte Analyse der Logdateien des Squid-Proxys

tweeper/bionic,bionic 1.2.0-1 all
  web scraper to convert supported websites like Twitter.com to RSS

```

All diese Moduel kann ich installieren. Für Joomla 4.0 benötige ich beispielsweise noch 
`php-ldap`. Dieses Modul installiere ich mit dem Befehl `sudo apt-get install php-ldap`.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt-get install php-ldap
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  php7.2-ldap
Die folgenden NEUEN Pakete werden installiert:
  php-ldap php7.2-ldap
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 25,6 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 114 kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 php7.2-ldap amd64 7.2.10-0ubuntu0.18.04.1 [23,6 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 php-ldap all 1:7.2+60ubuntu1 [2.000 B]
Es wurden 25,6 kB in 0 s geholt (161 kB/s).
Vormals nicht ausgewähltes Paket php7.2-ldap wird gewählt.
(Lese Datenbank ... 165240 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../php7.2-ldap_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-ldap (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php-ldap wird gewählt.
Vorbereitung zum Entpacken von .../php-ldap_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von php-ldap (1:7.2+60ubuntu1) ...
php7.2-ldap (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/ldap.ini with new version
php-ldap (1:7.2+60ubuntu1) wird eingerichtet ...
Trigger für libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1) werden verarbeitet ...
```

Ich kann mir die aktivierten Module mit dem Befehl `ls /etc/apache2/mods-enabled` ansehen.

```
astrid@astrid-TravelMate-5760G:~$ ls /etc/apache2/mods-enabled 
access_compat.load  authz_user.load  filter.load       php7.2.load
alias.conf          autoindex.conf   mime.conf         reqtimeout.conf
alias.load          autoindex.load   mime.load         reqtimeout.load
auth_basic.load     deflate.conf     mpm_prefork.conf  setenvif.conf
authn_core.load     deflate.load     mpm_prefork.load  setenvif.load
authn_file.load     dir.conf         negotiation.conf  status.conf
authz_core.load     dir.load         negotiation.load  status.load
authz_host.load     env.load         php7.2.conf
```

Huch, da ist ja mein eben installiertes `ldap`-Modul noch nicht dabei?  
Ich habe es auch noch nicht aktiviert. Ich aktiviere ein Module mit dem Befehl 
`sudo a2enmod Modulname`.

```
astrid@astrid-TravelMate-5760G:~$ sudo a2enmod ldap
Enabling module ldap.
To activate the new configuration, you need to run:
  systemctl restart apache2
```

Damit die Aktivierung wirksam wird, muss ich Apache2 mit dem Befehl `sudo systemctl restart apache2` 
neu starten.

```
astrid@astrid-TravelMate-5760G:~$ sudo systemctl restart apache2
```

Nach dem Neustart sehe ich das eben aktivierte Modul in der Liste der aktivierten Module.

```
astrid@astrid-TravelMate-5760G:~$ ls /etc/apache2/mods-enabled 
access_compat.load  autoindex.conf  ldap.load         reqtimeout.conf
alias.conf          autoindex.load  mime.conf         reqtimeout.load
alias.load          deflate.conf    mime.load         setenvif.conf
auth_basic.load     deflate.load    mpm_prefork.conf  setenvif.load
authn_core.load     dir.conf        mpm_prefork.load  status.conf
authn_file.load     dir.load        negotiation.conf  status.load
authz_core.load     env.load        negotiation.load
authz_host.load     filter.load     php7.2.conf
authz_user.load     ldap.conf       php7.2.load
```

Wenn ich mit ein paar Zeilen in der Datei `.htaccess` kurze und prägnante URLs 
generieren möchte benötige ich das Modul `mod_rewrite`. Dies nutzt Joomla zum Erzeugen 
der suchmaschinenfreudlichen URLs. Deshalb installiere ich dieses Modul als nächstes.

```
astrid@astrid-TravelMate-5760G:~$ sudo a2enmod rewrite 
Enabling module rewrite.
To activate the new configuration, you need to run:
  systemctl restart apache2
astrid@astrid-TravelMate-5760G:~$ sudo systemctl restart apache2
astrid@astrid-TravelMate-5760G:~$ ls /etc/apache2/mods-enabled 
access_compat.load  autoindex.conf  ldap.load         reqtimeout.conf
alias.conf          autoindex.load  mime.conf         reqtimeout.load
alias.load          deflate.conf    mime.load         rewrite.load
auth_basic.load     deflate.load    mpm_prefork.conf  setenvif.conf
authn_core.load     dir.conf        mpm_prefork.load  setenvif.load
authn_file.load     dir.load        negotiation.conf  status.conf
authz_core.load     env.load        negotiation.load  status.load
authz_host.load     filter.load     php7.2.conf
authz_user.load     ldap.conf       php7.2.load
```

Um mehr über die einzelnen Module zu erfahren, kann ich im Internet nach 
weiteren Informationen suchen. Ich kann auch die Beschreibung des 
Pakets ansehen, indem ich `apt show Paketname` eingebe.

```
astrid@astrid-TravelMate-5760G:~$ apt show php-cli
Package: php-cli
Version: 1:7.2+60ubuntu1
Priority: optional
Section: php
Source: php-defaults (60ubuntu1)
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian PHP Maintainers <pkg-php-maint@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 12,3 kB
Depends: php7.2-cli
Supported: 5y
Download-Size: 3.160 B
APT-Sources: http://de.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
Description: command-line interpreter for the PHP scripting language (default)
 This package provides the /usr/bin/php command interpreter, useful for
 testing PHP scripts from a shell or performing general shell scripting tasks.
 .
 PHP (recursive acronym for PHP: Hypertext Preprocessor) is a widely-used
 open source general-purpose scripting language that is especially suited
 for web development and can be embedded into HTML.
 .
 This package is a dependency package, which depends on Ubuntu's default
 PHP version (currently 7.2).
```

Nach meiner Erfahrung benötigt man für die Arbeit mit Joomla noch folgende Module:

```
sudo apt-get install php7.2-mysqli
sudo apt-get install php-pear
sudo apt-get install php7.2-mysql
sudo apt-get install php7.2-curl
sudo apt-get install php7.2-json
sudo apt-get install php7.2-cgi
sudo apt-get install php7.2
sudo apt-get install libapache2-mod-php7.2
sudo apt-get install php7.0-mcrypt
sudo apt-get install php-gd
sudo apt-get install php-zip
sudo /etc/init.d/apache2 restart
```

Nun ist mein LAMP-Stack installiert und konfiguriert. 
Bevor ich jedoch weitere Änderungen vornehme teste ich meine 
PHP-Konfiguration.

## Test der P H P-Konfiguration

Um zu testen, ob mein System ordnungsgemäß für PHP konfiguriert ist, 
erstelle ich ein sehr einfaches PHP-Skript namens `info.php`. 
Damit Apache die Datei mit dem Skript finden und korrekt bereitstellen kann, 
muss sie in einem speziellen Verzeichnis gespeichert werden. Dieses Verzeichnis wird oft als 
Stammverzeichnis[^3] bezeichnet.

In Ubuntu 18.04 mit Apache2 ist das Stammverzeichnis `/var/www/html/`. 
Ich erstelle meine Datei `info.php` und lege sie im Verzeichnis `/var/www/html/` ab. 
Ich wechsele also mit `cd /var/www/html/` in das Verzeichnis `/var/www/html/` und führe 
den Befehl `gedit info.php` aus.

```
astrid@astrid-TravelMate-5760G:~$ cd /var/www/html/
astrid@astrid-TravelMate-5760G:/var/www/html$ gedit info.php
```
Der Befehl `gedit info.php` öffnet eine leere Datei. 
Falls ich nicht die richtigen Berechtigungen habe, dazu später mehr, muss ich 
dem Befehl ein `sudo` voran stellen: `sudo gedit info.php`.
Ich fügen den folgenden Text in die Datei ein.

```
<?php
phpinfo();
?>
```
Wenn ich fertig bin, speichere und schließen ich die Datei.  

Jetzt kann ich testen, ob mein Webserver den von diesem PHP-Skript erzeugten 
Inhalt korrekt anzeigen kann. Außerdem kann ich die Konfiguration von PHP hier 
noch einmal - aufgelistet in einer Tabelle - überprüfen.
Um dies auszuprobieren, öffne ich also diese Datei in meinem Webbrowser. Ich gebe in der 
Adresszeile die Adresse `http://localhost/info.php` ein.

Das Ergebnis sollte wie folgt aussehen:

![Apache Standard Seite](../../media/2_Apache2_Ubuntu_Phpinfo_Page.png)


## Einstellungen für die Entwicklungsumgebung




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