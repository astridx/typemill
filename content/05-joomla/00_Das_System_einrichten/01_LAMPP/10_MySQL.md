# Mysql installieren

Nachdem ich meinen Webserver eingerichtet haben, ist es an der Zeit, 
MySQL zu installieren.   
MySQL ist ein Datenbankverwaltungssystem.   
MySQL organisiert und bietet Zugang zu den Datenbanken, 
in denen Joomla! dynamische Informationen speichert.

Ich verwende zu Installation von MySQL wieder APT.
`sudo apt install mysql-server` zeigt mir zu Beginn eine Liste der Pakete, 
die installiert werden, sowie den Speicherplatz, den sie belegen. 
Ich geben **J** ein, um fortzufahren.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install mysql-server
[sudo] Passwort für astrid: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libaio1 libevent-core-2.1-6 libhtml-template-perl mysql-client-5.7
  mysql-client-core-5.7 mysql-common mysql-server-5.7 mysql-server-core-5.7
Vorgeschlagene Pakete:
  libipc-sharedcache-perl mailx tinyca
Die folgenden NEUEN Pakete werden installiert:
  libaio1 libevent-core-2.1-6 libhtml-template-perl mysql-client-5.7
  mysql-client-core-5.7 mysql-common mysql-server mysql-server-5.7
  mysql-server-core-5.7
0 aktualisiert, 9 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 20,4 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 160 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 mysql-common all 5.8+1.0.4 [7.308 B]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libaio1 amd64 0.3.110-5 [6.448 B]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mysql-client-core-5.7 amd64 5.7.23-0ubuntu0.18.04.1 [6.985 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mysql-client-5.7 amd64 5.7.23-0ubuntu0.18.04.1 [2.312 kB]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mysql-server-core-5.7 amd64 5.7.23-0ubuntu0.18.04.1 [7.777 kB]
Holen:6 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libevent-core-2.1-6 amd64 2.1.8-stable-4build1 [85,9 kB]
Holen:7 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mysql-server-5.7 amd64 5.7.23-0ubuntu0.18.04.1 [3.194 kB]
Holen:8 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libhtml-template-perl all 2.97-1 [59,0 kB]
Holen:9 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 mysql-server all 5.7.23-0ubuntu0.18.04.1 [9.940 B]
Es wurden 20,4 MB in 7 s geholt (2.834 kB/s).                                  
Vorkonfiguration der Pakete ...
Vormals nicht ausgewähltes Paket mysql-common wird gewählt.
(Lese Datenbank ... 164813 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../0-mysql-common_5.8+1.0.4_all.deb ...
Entpacken von mysql-common (5.8+1.0.4) ...
Vormals nicht ausgewähltes Paket libaio1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../1-libaio1_0.3.110-5_amd64.deb ...
Entpacken von libaio1:amd64 (0.3.110-5) ...
Vormals nicht ausgewähltes Paket mysql-client-core-5.7 wird gewählt.
Vorbereitung zum Entpacken von .../2-mysql-client-core-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von mysql-client-core-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket mysql-client-5.7 wird gewählt.
Vorbereitung zum Entpacken von .../3-mysql-client-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von mysql-client-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket mysql-server-core-5.7 wird gewählt.
Vorbereitung zum Entpacken von .../4-mysql-server-core-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von mysql-server-core-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket libevent-core-2.1-6:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../5-libevent-core-2.1-6_2.1.8-stable-4build1_amd64.deb ...
Entpacken von libevent-core-2.1-6:amd64 (2.1.8-stable-4build1) ...
mysql-common (5.8+1.0.4) wird eingerichtet ...
update-alternatives: /etc/mysql/my.cnf.fallback wird verwendet, um /etc/mysql/my.cnf (my.cnf) im automatischen Modus bereitzustellen
Vormals nicht ausgewähltes Paket mysql-server-5.7 wird gewählt.
(Lese Datenbank ... 164981 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../mysql-server-5.7_5.7.23-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von mysql-server-5.7 (5.7.23-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket libhtml-template-perl wird gewählt.
Vorbereitung zum Entpacken von .../libhtml-template-perl_2.97-1_all.deb ...
Entpacken von libhtml-template-perl (2.97-1) ...
Vormals nicht ausgewähltes Paket mysql-server wird gewählt.
Vorbereitung zum Entpacken von .../mysql-server_5.7.23-0ubuntu0.18.04.1_all.deb ...
Entpacken von mysql-server (5.7.23-0ubuntu0.18.04.1) ...
libevent-core-2.1-6:amd64 (2.1.8-stable-4build1) wird eingerichtet ...
libhtml-template-perl (2.97-1) wird eingerichtet ...
Trigger für ureadahead (0.100.0-20) werden verarbeitet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
libaio1:amd64 (0.3.110-5) wird eingerichtet ...
Trigger für systemd (237-3ubuntu10.3) werden verarbeitet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
mysql-client-core-5.7 (5.7.23-0ubuntu0.18.04.1) wird eingerichtet ...
mysql-server-core-5.7 (5.7.23-0ubuntu0.18.04.1) wird eingerichtet ...
mysql-client-5.7 (5.7.23-0ubuntu0.18.04.1) wird eingerichtet ...
mysql-server-5.7 (5.7.23-0ubuntu0.18.04.1) wird eingerichtet ...
update-alternatives: /etc/mysql/mysql.cnf wird verwendet, um /etc/mysql/my.cnf (my.cnf) im automatischen Modus bereitzustellen
Renaming removed key_buffer and myisam-recover options (if present)
Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service → /lib/systemd/system/mysql.service.
mysql-server (5.7.23-0ubuntu0.18.04.1) wird eingerichtet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
Trigger für systemd (237-3ubuntu10.3) werden verarbeitet ...
Trigger für ureadahead (0.100.0-20) werden verarbeitet ...
```

> Hinweis: In diesem Fall muss ich `sudo apt update` nicht vor dem Installations-Befehl ausführen. 
Dies liegt daran, dass ich es kürzlich ausgeführt habe um Apache zu installieren. 
Der Paket-Index auf meinem Computer sollte also noch auf dem neuesten Stand sein.

Wenn die Installation abgeschlossen ist, führe ich ein einfaches 
Sicherheitsskript aus, das mit MySQL vorinstalliert ist. 
Dadurch werden einige gefährliche Standardeinstellungen entfernt und der 
Zugriff auf mein Datenbanksystem gesperrt. Auch wenn ich hier nur ein Testsystem 
installiere ist mir dies wichtig.

Ich starte das interaktive Skript, indem ich `sudo mysql_secure_installation` ausführen.
Als erstes werde ich gefragt, ob ich das `VALIDATE PASSWORD PLUGIN` 
konfigurieren möchte.

> Hinweis: Die Aktivierung dieser Funktion hat weitere Auswirkungen. 
Wenn diese Option aktiviert ist, werden Kennwörter, die den angegebenen 
Kriterien nicht entsprechen, von MySQL mit einem Fehler zurückgewiesen. 
Dies führt zu Problemen, wenn ich einmal ein schwaches Passwort in Verbindung mit 
einer Software verwendet wird, die automatisch MySQL-Anmeldeinformationen nutzt. 
Beispielsweise die Ubuntu-Pakete für phpMyAdmin. 

Alle weiteren Frage sind meiner Meinung nach gut erklärt.

```
astrid@astrid-TravelMate-5760G:~$ sudo mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No: Y

There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary                  file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0
Please set the password for root here.

New password: 

Re-enter new password: 

Estimated strength of the password: 100 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y 
Success.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y
Success.

By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y
 - Dropping test database...
Success.

 - Removing privileges on test database...
Success.

Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y
Success.

All done! 
```

Auf MySQL-Systemen ist der MySQL-Stammbenutzer `Root` standardmäßig so eingestellt, 
dass er sicher über das `auth_socket-Plugin` authentifiziert und nicht mit einem Passwort. 
Dies ermöglicht in einigen Fällen eine größere Sicherheit und Benutzerfreundlichkeit, 
aber es kann auch Dinge komplizieren. Zum Beispiel, wenn ich mit einem externen Programm 
wie phpMyAdmin arbeite.

Ich bevorzuge bei der Verbindung zu MySQL als Root ein Passwort. Deshalb muss 
ich die Authentifizierungsmethode von `auth_socket` auf `mysql_native_password` umstellen. 
Dazu öffne ich die MySQL-Eingabeaufforderung von meinem Terminal aus mit dem Befehl 
`sudo mysql`.

```
astrid@astrid-TravelMate-5760G:~$ sudo mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.23-0ubuntu0.18.04.1 (Ubuntu)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Als nächstes überprüfe ich, welche Authentifizierungsmethode jedes meiner 
MySQL-Benutzerkonten verwendet:

```
mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
+------------------+-------------------------------------------+-----------------------+-----------+
| user             | authentication_string                     | plugin                | host      |
+------------------+-------------------------------------------+-----------------------+-----------+
| root             |                                           | auth_socket           | localhost |
| mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| debian-sys-maint | *016566FD9ECFB632C3F96B1CC29B39B475FD8F5E | mysql_native_password | localhost |
+------------------+-------------------------------------------+-----------------------+-----------+
4 rows in set (0.00 sec)
```

Der Benutzer `root` authentifiziert sich tatsächlich mithilfe des Plugins `auth_socket`. 
Ich führe den Befehl `ALTER USER` aus, um das root-Konto für die 
Authentifizierung mit einem Kennwort zu konfigurieren. Dabei achte ich darauf, 
das ich ein sicheres Passwort wähle.

```
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SicheresPasswort!1';
Query OK, 0 rows affected (0.00 sec)
```
Zuletzt lade ich die Grant-Tabellen mit FLUSH PRIVILEGES neu, damit meine Änderungen 
übernommen werden.

```
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)
```
Ich überprüfe die die Authentifizierungsmethoden. Dies tue ich um sicher zu 
gehen, dass sich der Benutzer `root` nicht mehr mit dem Plugin auth_socket authentifiziert.


```
mysql> SELECT user,authentication_string,plugin,host FROM mysql.user;
+------------------+-------------------------------------------+-----------------------+-----------+
| user             | authentication_string                     | plugin                | host      |
+------------------+-------------------------------------------+-----------------------+-----------+
| root             | *86F726D2F65279C6266A8182B8A5EE8393C7CB0A | mysql_native_password | localhost |
| mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| debian-sys-maint | *016566FD9ECFB632C3F96B1CC29B39B475FD8F5E | mysql_native_password | localhost |
+------------------+-------------------------------------------+-----------------------+-----------+
4 rows in set (0.00 sec)
```

Ich sehe, dass sich der `root-MySQL-Benutzer` nun mit 
einem Passwort authentifiziert. 
Nun kann ich die MySQL-Shell mit `exit` beenden.

```
mysql> exit
Bye
```

Mein Datenbanksystem ist nun eingerichtet und ich kann mit der Installation von 
PHP, der letzten Komponente des LAMP-Stacks, fortfahren.

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