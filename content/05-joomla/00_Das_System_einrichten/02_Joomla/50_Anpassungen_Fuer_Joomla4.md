# Anpassungen für Joomla 4

## Joomla 4

### Den Joomla 4 Branch in Git finden

Im Moment wird standardmäßig der Git-Zweig zu Joomla 3 angeboten. 
Dies habe ich im letzten Kapitel praktisch erfahren. Ich möchte aber Joomla 4 
testen. Dieser Joomla 4 Zweit ist natürlich auch verfügbar. Hier zeige ich, wie ich auf diesen 
Zweig wechsele.

Zunächst stelle ich sicher, dass ich mich im richtigen Verzeichnis befinde. Bei mir ist 
dies `/var/www/html/joomla-cms/`. 

```
astrid@astrid-TravelMate-5760G:~$ cd /var/www/html/joomla-cms/
```

Danach sehe ich mir den aktuellen Status an. Ich habe noch nichts geändert, deshalb 
ist mein Zweig auch noch unverändert.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git status
Auf Branch staging
Ihr Branch ist auf demselben Stand wie 'origin/staging'.

nichts zu committen, Arbeitsverzeichnis unverändert
```

> Ungewollte Änderungen kann man mit dem Befehl `git stash`[^10] oder dem Befehl 
`git clean -fd`[^11] wieder rückgängig machen. 
Aber Achtung: Damit sind die Änderungen wirklich weg!

Nun will ich überprüfen, auf welchem Zweig ich mich gerade befinde. Ich finde das 
zur Orientierung immer sehr hilfreich.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git branch
* staging
```

OK, ich bin auf dem Zweig mit dem Namen `staging`. Das ist richtig. So heißt der Zweig, auf 
dem die aktuelle Arbeitsversion von Joomla! sich befindet.  

Bisher habe ich nur Git Daten von Joomla verwendet. Ich habe ein entferntes Repositiory 
eingebunden. Dies sehe ich mir nun auch einmal genauer an. Der Befehl `git remote show` zeigt 
mir die Namen der entfernten Repositorien. Das Joomla Repository wurde unter dem Namen 
`origin` eingebunden. Ich lasse diesen Namen. Joomlaner nennen das Repository in der Regel 
`upload`.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git remote show 
origin
```

Als nächste möchte ich mir ansehen, das auch wirklich die richtige Adresse hinter dem Namen
`origin` steckt. Hierfür verwende ich den Befehl `git remote show origin`.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git remote show origin
* Remote-Repository origin
  URL zum Abholen: https://github.com/joomla/joomla-cms.git
  URL zum Versenden: https://github.com/joomla/joomla-cms.git
  Hauptbranch: staging
  Remote-Branches:
    3.10-dev      gefolgt
    4.0-dev       gefolgt
    l10n_4.0-dev  gefolgt
    l10n_4.0-dev2 gefolgt
    l10n_staging  gefolgt
    staging       gefolgt
  Lokaler Branch konfiguriert für 'git pull':
    staging führt mit Remote-Branch staging zusammen
  Lokale Referenz konfiguriert für 'git push':
    staging versendet nach staging (aktuell)
```

Ja, die URL passt und ich kann auch alle verfügbaren Zweige sehen.

> Mein eigenes Repository kann ich mit dem Befehl 
`git remote add SelbstvergebenerName https://github.com/astridx/joomla-cms.git` 
hinzufügen. Dazu aber später mehr.

Ich möchte nun auf den Zweig, in dem sich die Dateien zu Joomla 4 befinden, wechseln. Dazu 
hole ich mir mit dem Befehl `git fetch origin 4.0-dev:4.0-dev` diesen Zweig auf meinen lokalen 
Rechner.  

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git fetch origin 4.0-dev:4.0-dev 
Von https://github.com/joomla/joomla-cms
 * [neuer Branch]          4.0-dev    -> 4.0-dev
```

Das der Zweig angekommen ist, kann ich mit `git branch` überprüfen. 

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git branch
  4.0-dev
* staging
```

Der Zweig `4.0-dev` ist angekommen. Der Stern neben dem Zweig `staging` zeigt mir, 
dass ich mich gerade auf dem Zweig `staging` befinde. Mit `git checkout 4.0-dev` wechsele ich den Zweig.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git checkout 4.0-dev 
Zu Branch '4.0-dev' gewechselt
```
Ich traue keinem Befehl. Deshalb überprüfe ich auch, ob der Wechsel korrekt erfolgt ist.

```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git branch
* 4.0-dev
  staging
```

Nun möchte ich mir sofort Joomla 4 im Webbrowser ansehen. Und hier stelle ich fest, 
dass ich für Joomla 4 noch einige Konfiguratiosschritte vornehmen muss[^12].

![Apache Standard Seite](../../media/4_Joomla_Environment_Setup.png)

### Die aktuellste Version des Composers unter Ubuntu 18.04 installieren

Meine Installationsschritte habe ich von dieser Website abgeguckt:
https://getcomposer.org/download/

Ich starte, wie schon im LAMP-Teil erklärt, mit `sudo apt update` um sicher zu gehen, 
das meine Installationsquellen auf dem neuesten Stand sind.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt update
Holen:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
OK:2 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease         
OK:3 http://de.archive.ubuntu.com/ubuntu bionic InRelease                      
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]
Holen:6 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [401 kB]
Holen:7 http://de.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [362 kB]
Holen:8 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [173 kB]
Holen:9 http://de.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [40,8 kB]
Holen:10 http://de.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [81,8 kB]
Holen:11 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [555 kB]
Holen:12 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [560 kB]
OK:13 https://deb.nodesource.com/node_8.x bionic InRelease                     
Holen:14 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [183 kB]
Holen:15 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [181 kB]
Holen:16 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [291 kB]
Holen:17 http://de.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.464 B]
Holen:18 http://de.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5.100 B]
Es wurden 3.082 kB in 3 s geholt (1.075 kB/s).                           
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Alle Pakete sind aktuell.
```
Danach installiere ich Module, von denen ich weiß, dass ich sie für die Arbeit mit Composer benötigen werde.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install curl php-cli php-mbstring git unzip
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
unzip ist schon die neueste Version (6.0-21ubuntu1).
git ist schon die neueste Version (1:2.17.1-1ubuntu0.3).
Die folgenden zusätzlichen Pakete werden installiert:
  php7.2-mbstring
Die folgenden NEUEN Pakete werden installiert:
  curl php-cli php-mbstring php7.2-mbstring
0 aktualisiert, 4 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 647 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 2.131 kB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 curl amd64 7.58.0-2ubuntu3.3 [159 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 php-cli all 1:7.2+60ubuntu1 [3.160 B]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 php7.2-mbstring amd64 7.2.10-0ubuntu0.18.04.1 [483 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 php-mbstring all 1:7.2+60ubuntu1 [2.008 B]
Es wurden 647 kB in 1 s geholt (1.274 kB/s).
Vormals nicht ausgewähltes Paket curl wird gewählt.
(Lese Datenbank ... 166382 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../curl_7.58.0-2ubuntu3.3_amd64.deb ...
Entpacken von curl (7.58.0-2ubuntu3.3) ...
Vormals nicht ausgewähltes Paket php-cli wird gewählt.
Vorbereitung zum Entpacken von .../php-cli_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von php-cli (1:7.2+60ubuntu1) ...
Vormals nicht ausgewähltes Paket php7.2-mbstring wird gewählt.
Vorbereitung zum Entpacken von .../php7.2-mbstring_7.2.10-0ubuntu0.18.04.1_amd64.deb ...
Entpacken von php7.2-mbstring (7.2.10-0ubuntu0.18.04.1) ...
Vormals nicht ausgewähltes Paket php-mbstring wird gewählt.
Vorbereitung zum Entpacken von .../php-mbstring_1%3a7.2+60ubuntu1_all.deb ...
Entpacken von php-mbstring (1:7.2+60ubuntu1) ...
curl (7.58.0-2ubuntu3.3) wird eingerichtet ...
php7.2-mbstring (7.2.10-0ubuntu0.18.04.1) wird eingerichtet ...

Creating config file /etc/php/7.2/mods-available/mbstring.ini with new version
php-cli (1:7.2+60ubuntu1) wird eingerichtet ...
php-mbstring (1:7.2+60ubuntu1) wird eingerichtet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
Trigger für libapache2-mod-php7.2 (7.2.10-0ubuntu0.18.04.1) werden verarbeitet ...
```

Nun wechsele ich in mein Homeverzeichnis

```
astrid@astrid-TravelMate-5760G:~$ cd ~
```

Ich lade das Installationsprogramm in das aktuelle Verzeichnis herunter.

```
astrid@astrid-TravelMate-5760G:~$ php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```

Ich überprüfe das Installationsprogramm.

```
astrid@astrid-TravelMate-5760G:~$ php -r "if (hash_file('SHA384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```

Ich führe das Installationsprogramm aus.

```
astrid@astrid-TravelMate-5760G:~$ php composer-setup.php
All settings correct for using Composer
Downloading...

Composer (version 1.7.2) successfully installed to: /home/astrid/composer.phar
Use it: php composer.phar
```

Ich entfernen das Installationsprogramm wieder.
```
astrid@astrid-TravelMate-5760G:~$ php -r "unlink('composer-setup.php');"
``` 

Ich teste die Installation von Composer indem ich einfach den Befehl `composer` eingebe.

```
astrid@astrid-TravelMate-5760G:~$ composer
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.7.2 2018-08-16 16:57:12

Usage:
  command [options] [arguments]

Options:
  -h, --help                     Display this help message
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version
      --ansi                     Force ANSI output
      --no-ansi                  Disable ANSI output
  -n, --no-interaction           Do not ask any interactive question
      --profile                  Display timing and memory usage information
      --no-plugins               Whether to disable plugins.
  -d, --working-dir=WORKING-DIR  If specified, use the given directory as working directory.
  -v|vv|vvv, --verbose           Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Available commands:
  about                Shows the short information about Composer.
  archive              Creates an archive of this composer package.
  browse               Opens the package's repository URL or homepage in your browser.
  check-platform-reqs  Check that platform requirements are satisfied.
  clear-cache          Clears composer's internal package cache.
  clearcache           Clears composer's internal package cache.
  config               Sets config options.
  create-project       Creates new project from a package into given directory.
  depends              Shows which packages cause the given package to be installed.
  diagnose             Diagnoses the system to identify common errors.
  dump-autoload        Dumps the autoloader.
  dumpautoload         Dumps the autoloader.
  exec                 Executes a vendored binary/script.
  global               Allows running commands in the global composer dir ($COMPOSER_HOME).
  help                 Displays help for a command
  home                 Opens the package's repository URL or homepage in your browser.
  i                    Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.
  info                 Shows information about packages.
  init                 Creates a basic composer.json file in current directory.
  install              Installs the project dependencies from the composer.lock file if present, or falls back on the composer.json.
  licenses             Shows information about licenses of dependencies.
  list                 Lists commands
  outdated             Shows a list of installed packages that have updates available, including their latest version.
  prohibits            Shows which packages prevent the given package from being installed.
  remove               Removes a package from the require or require-dev.
  require              Adds required packages to your composer.json and installs them.
  run-script           Runs the scripts defined in composer.json.
  search               Searches for packages.
  self-update          Updates composer.phar to the latest version.
  selfupdate           Updates composer.phar to the latest version.
  show                 Shows information about packages.
  status               Shows a list of locally modified packages, for packages installed from source.
  suggests             Shows package suggestions.
  u                    Upgrades your dependencies to the latest version according to composer.json, and updates the composer.lock file.
  update               Upgrades your dependencies to the latest version according to composer.json, and updates the composer.lock file.
  upgrade              Upgrades your dependencies to the latest version according to composer.json, and updates the composer.lock file.
  validate             Validates a composer.json and composer.lock.
  why                  Shows which packages cause the given package to be installed.
  why-not              Shows which packages prevent the given package from being installed.
astrid@astrid-TravelMate-5760G:~$ 
```



### Node.js und NPM

Node.js ist eine JavaScript-Plattform für allgemeine Programmierung, 
mit der Benutzer Anwendungen für die Zusammenarbeit in Computernetzen erstellen können. 
Durch die Nutzung von JavaScript sowohl im Front- als auch im Backend wird 
die Entwicklung von Node.js konsistenter und integrierter.

Hier schreibe ich, wie ich mit Node.js auf einem Ubuntu 18.04-Server installiert habe.

Ich starte, wie  im LAMP-Teil erklärt, mit `sudo apt update` um sicher zu gehen, 
das meine Installationsquellen auf dem neuesten Stand sind.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt update
[sudo] Passwort für astrid: 
Holen:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
OK:2 http://de.archive.ubuntu.com/ubuntu bionic InRelease                      
OK:3 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease         
OK:4 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease              
OK:5 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease            
OK:6 https://deb.nodesource.com/node_8.x bionic InRelease     
Es wurden 83,2 kB in 1 s geholt (61,6 kB/s).
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Alle Pakete sind aktuell.
```

Als nächstes installiere ich Node.js aus den Repositories.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install nodejs
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  libc-ares2 libhttp-parser2.7.1 libuv1 nodejs-doc
Die folgenden NEUEN Pakete werden installiert:
  libc-ares2 libhttp-parser2.7.1 libuv1 nodejs nodejs-doc
0 aktualisiert, 5 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen 5.671 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 24,8 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libuv1 amd64 1.18.0-3 [64,4 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 nodejs-doc all 8.10.0~dfsg-2ubuntu0.3 [752 kB]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libc-ares2 amd64 1.14.0-1 [37,1 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libhttp-parser2.7.1 amd64 2.7.1-2 [20,6 kB]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 nodejs amd64 8.10.0~dfsg-2ubuntu0.3 [4.796 kB]
Es wurden 5.671 kB in 4 s geholt (1.268 kB/s).
Vormals nicht ausgewähltes Paket libuv1:amd64 wird gewählt.
(Lese Datenbank ... 166404 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../libuv1_1.18.0-3_amd64.deb ...
Entpacken von libuv1:amd64 (1.18.0-3) ...
Vormals nicht ausgewähltes Paket nodejs-doc wird gewählt.
Vorbereitung zum Entpacken von .../nodejs-doc_8.10.0~dfsg-2ubuntu0.3_all.deb ...
Entpacken von nodejs-doc (8.10.0~dfsg-2ubuntu0.3) ...
Vormals nicht ausgewähltes Paket libc-ares2:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libc-ares2_1.14.0-1_amd64.deb ...
Entpacken von libc-ares2:amd64 (1.14.0-1) ...
Vormals nicht ausgewähltes Paket libhttp-parser2.7.1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libhttp-parser2.7.1_2.7.1-2_amd64.deb ...
Entpacken von libhttp-parser2.7.1:amd64 (2.7.1-2) ...
Vormals nicht ausgewähltes Paket nodejs wird gewählt.
Vorbereitung zum Entpacken von .../nodejs_8.10.0~dfsg-2ubuntu0.3_amd64.deb ...
Entpacken von nodejs (8.10.0~dfsg-2ubuntu0.3) ...
nodejs-doc (8.10.0~dfsg-2ubuntu0.3) wird eingerichtet ...
libhttp-parser2.7.1:amd64 (2.7.1-2) wird eingerichtet ...
libuv1:amd64 (1.18.0-3) wird eingerichtet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
libc-ares2:amd64 (1.14.0-1) wird eingerichtet ...
nodejs (8.10.0~dfsg-2ubuntu0.3) wird eingerichtet ...
update-alternatives: /usr/bin/nodejs wird verwendet, um /usr/bin/js (js) im automatischen Modus bereitzustellen
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
```

Ich möchten auch npm, den Paketmanager von Node.js, installieren. 
Ich kann dies tun, indem ich `sudo apt install npm` eingebe.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install npm
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  build-essential dpkg-dev fakeroot g++ g++-7 gcc gcc-7 gyp javascript-common
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan4 libatomic1 libc-dev-bin libc6-dev libcilkrts5 libfakeroot
  libgcc-7-dev libitm1 libjs-async libjs-inherits libjs-jquery libjs-node-uuid
  libjs-underscore liblsan0 libmpx2 libpython-stdlib libquadmath0
  libssl1.0-dev libstdc++-7-dev libtsan0 libubsan0 libuv1-dev linux-libc-dev
  make manpages-dev node-abbrev node-ansi node-ansi-color-table node-archy
  node-async node-balanced-match node-block-stream node-brace-expansion
  node-builtin-modules node-combined-stream node-concat-map node-cookie-jar
  node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob
  node-graceful-fs node-gyp node-hosted-git-info node-inflight node-inherits
  node-ini node-is-builtin-module node-isexe node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-path-is-absolute node-pseudomap
  node-qs node-read node-read-package-json node-request node-retry node-rimraf
  node-semver node-sha node-slide node-spdx-correct node-spdx-expression-parse
  node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist
  nodejs-dev python python-minimal python-pkg-resources python2.7
  python2.7-minimal
Vorgeschlagene Pakete:
  debian-keyring g++-multilib g++-7-multilib gcc-7-doc libstdc++6-7-dbg
  gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-7-multilib
  gcc-7-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg
  libasan4-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg
  libmpx2-dbg libquadmath0-dbg glibc-doc libstdc++-7-doc make-doc node-hawk
  node-aws-sign node-oauth-sign node-http-signature debhelper python-doc
  python-tk python-setuptools python2.7-doc binfmt-support
Die folgenden NEUEN Pakete werden installiert:
  build-essential dpkg-dev fakeroot g++ g++-7 gcc gcc-7 gyp javascript-common
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan4 libatomic1 libc-dev-bin libc6-dev libcilkrts5 libfakeroot
  libgcc-7-dev libitm1 libjs-async libjs-inherits libjs-jquery libjs-node-uuid
  libjs-underscore liblsan0 libmpx2 libpython-stdlib libquadmath0
  libssl1.0-dev libstdc++-7-dev libtsan0 libubsan0 libuv1-dev linux-libc-dev
  make manpages-dev node-abbrev node-ansi node-ansi-color-table node-archy
  node-async node-balanced-match node-block-stream node-brace-expansion
  node-builtin-modules node-combined-stream node-concat-map node-cookie-jar
  node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob
  node-graceful-fs node-gyp node-hosted-git-info node-inflight node-inherits
  node-ini node-is-builtin-module node-isexe node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-path-is-absolute node-pseudomap
  node-qs node-read node-read-package-json node-request node-retry node-rimraf
  node-semver node-sha node-slide node-spdx-correct node-spdx-expression-parse
  node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist
  nodejs-dev npm python python-minimal python-pkg-resources python2.7
  python2.7-minimal
0 aktualisiert, 106 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
Es müssen noch 31,3 MB von 33,0 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 147 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libc-dev-bin amd64 2.27-3ubuntu1 [71,8 kB]
Holen:2 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-libc-dev amd64 4.15.0-36.39 [999 kB]
Holen:3 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libc6-dev amd64 2.27-3ubuntu1 [2.587 kB]
Holen:4 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libitm1 amd64 8.2.0-1ubuntu2~18.04 [28,1 kB]
Holen:5 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libatomic1 amd64 8.2.0-1ubuntu2~18.04 [9.064 B]
Holen:6 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libasan4 amd64 7.3.0-27ubuntu1~18.04 [358 kB]
Holen:7 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 liblsan0 amd64 8.2.0-1ubuntu2~18.04 [132 kB]
Holen:8 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libtsan0 amd64 8.2.0-1ubuntu2~18.04 [288 kB]
Holen:9 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libubsan0 amd64 7.3.0-27ubuntu1~18.04 [126 kB]
Holen:10 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libcilkrts5 amd64 7.3.0-27ubuntu1~18.04 [42,5 kB]
Holen:11 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libmpx2 amd64 8.2.0-1ubuntu2~18.04 [11,7 kB]
Holen:12 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libquadmath0 amd64 8.2.0-1ubuntu2~18.04 [133 kB]
Holen:13 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libgcc-7-dev amd64 7.3.0-27ubuntu1~18.04 [2.380 kB]
Holen:14 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gcc-7 amd64 7.3.0-27ubuntu1~18.04 [7.455 kB]
Holen:15 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 gcc amd64 4:7.3.0-3ubuntu2.1 [5.184 B]
Holen:16 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libstdc++-7-dev amd64 7.3.0-27ubuntu1~18.04 [1.463 kB]
Holen:17 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 g++-7 amd64 7.3.0-27ubuntu1~18.04 [7.570 kB]
Holen:18 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 g++ amd64 4:7.3.0-3ubuntu2.1 [1.572 B]
Holen:19 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 make amd64 4.1-9.1ubuntu1 [154 kB]
Holen:20 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 dpkg-dev all 1.19.0.5ubuntu2 [607 kB]
Holen:21 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 build-essential amd64 12.4ubuntu1 [4.758 B]
Holen:22 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libfakeroot amd64 1.22-2ubuntu1 [25,9 kB]
Holen:23 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 fakeroot amd64 1.22-2ubuntu1 [62,3 kB]
Holen:24 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 python-pkg-resources all 39.0.1-2 [128 kB]
Holen:25 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 gyp all 0.1+20150913git1f374df9-1ubuntu1 [265 kB]
Holen:26 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 javascript-common all 11 [6.066 B]
Holen:27 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libalgorithm-diff-perl all 1.19.03-1 [47,6 kB]
Holen:28 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libalgorithm-diff-xs-perl amd64 0.04-5 [11,1 kB]
Holen:29 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libalgorithm-merge-perl all 0.08-3 [12,0 kB]
Holen:30 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 libjs-async all 0.8.0-3 [25,4 kB]
Holen:31 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libjs-jquery all 3.2.1-1 [152 kB]
Holen:32 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 libjs-node-uuid all 1.4.7-5 [11,5 kB]
Holen:33 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libjs-underscore all 1.8.3~dfsg-1 [59,9 kB]
Holen:34 http://de.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libssl1.0-dev amd64 1.0.2n-1ubuntu5.1 [1.364 kB]
Holen:35 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 libuv1-dev amd64 1.18.0-3 [82,0 kB]
Holen:36 http://de.archive.ubuntu.com/ubuntu bionic/main amd64 manpages-dev all 4.15-1 [2.217 kB]
Holen:37 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-async all 0.8.0-3 [2.840 B]
Holen:38 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-builtin-modules all 1.1.1-1 [3.338 B]
Holen:39 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-fs.realpath all 1.0.0-1 [5.572 B]
Holen:40 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-hosted-git-info all 2.5.0-1 [6.756 B]
Holen:41 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-wrappy all 1.0.2-1 [3.162 B]
Holen:42 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-once all 1.4.0-2ubuntu1 [3.588 B]
Holen:43 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-inflight all 1.0.6-1 [3.382 B]
Holen:44 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-is-builtin-module all 1.0.0-1 [2.906 B]
Holen:45 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-isexe all 2.0.0-3 [4.376 B]
Holen:46 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-node-uuid all 1.4.7-5 [2.844 B]
Holen:47 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-path-is-absolute all 1.0.0-1 [3.310 B]
Holen:48 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-pseudomap all 1.0.2-1 [3.534 B]
Holen:49 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-spdx-license-ids all 1.2.2-1 [4.792 B]
Holen:50 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-spdx-correct all 1.0.2-1 [3.718 B]
Holen:51 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-spdx-expression-parse all 1.0.4-1 [12,1 kB]
Holen:52 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-underscore all 1.8.3~dfsg-1 [3.790 B]
Holen:53 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-validate-npm-package-license all 3.0.1-1 [3.488 B]
Holen:54 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-yallist all 2.0.0-1 [5.398 B]
Holen:55 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 libjs-inherits all 2.0.3-1 [2.792 B]
Holen:56 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-abbrev all 1.0.9-1 [3.708 B]
Holen:57 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-ansi all 0.3.0-2ubuntu1 [8.720 B]
Holen:58 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-ansi-color-table all 1.0.0-1 [4.478 B]
Holen:59 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-archy all 1.0.0-1ubuntu1 [4.264 B]
Holen:60 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-balanced-match all 0.4.2-1 [4.030 B]
Holen:61 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-inherits all 2.0.3-1 [3.092 B]
Holen:62 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-block-stream all 0.0.9-1ubuntu1 [4.736 B]
Holen:63 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-concat-map all 0.0.1-1 [3.502 B]
Holen:64 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-brace-expansion all 1.1.8-1 [5.840 B]
Holen:65 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-delayed-stream all 0.0.5-1 [4.750 B]
Holen:66 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-combined-stream all 0.0.5-1 [4.958 B]
Holen:67 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-cookie-jar all 0.3.1-1 [3.746 B]
Holen:68 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-forever-agent all 0.5.1-1 [3.194 B]
Holen:69 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-mime all 1.3.4-1 [11,9 kB]
Holen:70 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-form-data all 0.1.0-1 [6.412 B]
Holen:71 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-minimatch all 3.0.4-3 [13,5 kB]
Holen:72 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-glob all 7.1.2-4 [17,7 kB]
Holen:73 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-rimraf all 2.6.2-1 [8.152 B]
Holen:74 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-mkdirp all 0.5.1-1 [4.848 B]
Holen:75 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-graceful-fs all 4.1.11-1 [10,8 kB]
Holen:76 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-fstream all 1.0.10-1 [18,1 kB]
Holen:77 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-fstream-ignore all 0.0.6-2 [5.586 B]
Holen:78 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-github-url-from-git all 1.4.0-1 [3.782 B]
Holen:79 http://de.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 nodejs-dev amd64 8.10.0~dfsg-2ubuntu0.3 [351 kB]
Holen:80 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-nopt all 3.0.6-3 [9.572 B]
Holen:81 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-npmlog all 0.0.4-1 [5.844 B]
Holen:82 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-osenv all 0.1.4-1 [4.212 B]
Holen:83 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-tunnel-agent all 0.3.1-1 [4.018 B]
Holen:84 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-json-stringify-safe all 5.0.0-1 [3.544 B]
Holen:85 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-qs all 2.2.4-1ubuntu1 [7.680 B]
Holen:86 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-request all 2.26.1-1 [14,5 kB]
Holen:87 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-semver all 5.4.1-1 [22,6 kB]
Holen:88 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-tar all 2.2.1-1 [17,7 kB]
Holen:89 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-which all 1.3.0-1 [4.504 B]
Holen:90 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-gyp all 3.6.2-1ubuntu1 [29,4 kB]
Holen:91 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-ini all 1.3.4-1 [5.588 B]
Holen:92 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-lockfile all 0.4.1-1 [5.450 B]
Holen:93 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-lru-cache all 4.1.1-1 [8.228 B]
Holen:94 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-mute-stream all 0.0.7-1 [4.372 B]
Holen:95 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-normalize-package-data all 2.3.5-2 [10,6 kB]
Holen:96 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-read all 1.0.7-1 [4.572 B]
Holen:97 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-read-package-json all 1.2.4-1 [7.780 B]
Holen:98 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-retry all 0.10.1-1 [8.016 B]
Holen:99 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-sha all 1.2.3-1 [4.272 B]
Holen:100 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 node-slide all 1.1.6-1 [6.212 B]
Holen:101 http://de.archive.ubuntu.com/ubuntu bionic/universe amd64 npm all 3.5.2-0ubuntu4 [1.586 kB]
Es wurden 31,3 MB in 11 s geholt (2.740 kB/s).                                 
Extrahiere Vorlagen aus Paketen: 100%
Vormals nicht ausgewähltes Paket python2.7-minimal wird gewählt.
(Lese Datenbank ... 166545 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../python2.7-minimal_2.7.15~rc1-1_amd64.deb ...
Entpacken von python2.7-minimal (2.7.15~rc1-1) ...
Vormals nicht ausgewähltes Paket python-minimal wird gewählt.
Vorbereitung zum Entpacken von .../python-minimal_2.7.15~rc1-1_amd64.deb ...
Entpacken von python-minimal (2.7.15~rc1-1) ...
Vormals nicht ausgewähltes Paket python2.7 wird gewählt.
Vorbereitung zum Entpacken von .../python2.7_2.7.15~rc1-1_amd64.deb ...
Entpacken von python2.7 (2.7.15~rc1-1) ...
Vormals nicht ausgewähltes Paket libpython-stdlib:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../libpython-stdlib_2.7.15~rc1-1_amd64.deb ...
Entpacken von libpython-stdlib:amd64 (2.7.15~rc1-1) ...
python2.7-minimal (2.7.15~rc1-1) wird eingerichtet ...
Linking and byte-compiling packages for runtime python2.7...
python-minimal (2.7.15~rc1-1) wird eingerichtet ...
Vormals nicht ausgewähltes Paket python wird gewählt.
(Lese Datenbank ... 166601 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../000-python_2.7.15~rc1-1_amd64.deb ...
Entpacken von python (2.7.15~rc1-1) ...
Vormals nicht ausgewähltes Paket libc-dev-bin wird gewählt.
Vorbereitung zum Entpacken von .../001-libc-dev-bin_2.27-3ubuntu1_amd64.deb ...
Entpacken von libc-dev-bin (2.27-3ubuntu1) ...
Vormals nicht ausgewähltes Paket linux-libc-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../002-linux-libc-dev_4.15.0-36.39_amd64.deb ...
Entpacken von linux-libc-dev:amd64 (4.15.0-36.39) ...
Vormals nicht ausgewähltes Paket libc6-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../003-libc6-dev_2.27-3ubuntu1_amd64.deb ...
Entpacken von libc6-dev:amd64 (2.27-3ubuntu1) ...
Vormals nicht ausgewähltes Paket libitm1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../004-libitm1_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von libitm1:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libatomic1:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../005-libatomic1_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von libatomic1:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libasan4:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../006-libasan4_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von libasan4:amd64 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket liblsan0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../007-liblsan0_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von liblsan0:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libtsan0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../008-libtsan0_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von libtsan0:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libubsan0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../009-libubsan0_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von libubsan0:amd64 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket libcilkrts5:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../010-libcilkrts5_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von libcilkrts5:amd64 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket libmpx2:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../011-libmpx2_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von libmpx2:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libquadmath0:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../012-libquadmath0_8.2.0-1ubuntu2~18.04_amd64.deb ...
Entpacken von libquadmath0:amd64 (8.2.0-1ubuntu2~18.04) ...
Vormals nicht ausgewähltes Paket libgcc-7-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../013-libgcc-7-dev_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von libgcc-7-dev:amd64 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket gcc-7 wird gewählt.
Vorbereitung zum Entpacken von .../014-gcc-7_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von gcc-7 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket gcc wird gewählt.
Vorbereitung zum Entpacken von .../015-gcc_4%3a7.3.0-3ubuntu2.1_amd64.deb ...
Entpacken von gcc (4:7.3.0-3ubuntu2.1) ...
Vormals nicht ausgewähltes Paket libstdc++-7-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../016-libstdc++-7-dev_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von libstdc++-7-dev:amd64 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket g++-7 wird gewählt.
Vorbereitung zum Entpacken von .../017-g++-7_7.3.0-27ubuntu1~18.04_amd64.deb ...
Entpacken von g++-7 (7.3.0-27ubuntu1~18.04) ...
Vormals nicht ausgewähltes Paket g++ wird gewählt.
Vorbereitung zum Entpacken von .../018-g++_4%3a7.3.0-3ubuntu2.1_amd64.deb ...
Entpacken von g++ (4:7.3.0-3ubuntu2.1) ...
Vormals nicht ausgewähltes Paket make wird gewählt.
Vorbereitung zum Entpacken von .../019-make_4.1-9.1ubuntu1_amd64.deb ...
Entpacken von make (4.1-9.1ubuntu1) ...
Vormals nicht ausgewähltes Paket dpkg-dev wird gewählt.
Vorbereitung zum Entpacken von .../020-dpkg-dev_1.19.0.5ubuntu2_all.deb ...
Entpacken von dpkg-dev (1.19.0.5ubuntu2) ...
Vormals nicht ausgewähltes Paket build-essential wird gewählt.
Vorbereitung zum Entpacken von .../021-build-essential_12.4ubuntu1_amd64.deb ...
Entpacken von build-essential (12.4ubuntu1) ...
Vormals nicht ausgewähltes Paket libfakeroot:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../022-libfakeroot_1.22-2ubuntu1_amd64.deb ...
Entpacken von libfakeroot:amd64 (1.22-2ubuntu1) ...
Vormals nicht ausgewähltes Paket fakeroot wird gewählt.
Vorbereitung zum Entpacken von .../023-fakeroot_1.22-2ubuntu1_amd64.deb ...
Entpacken von fakeroot (1.22-2ubuntu1) ...
Vormals nicht ausgewähltes Paket python-pkg-resources wird gewählt.
Vorbereitung zum Entpacken von .../024-python-pkg-resources_39.0.1-2_all.deb ...
Entpacken von python-pkg-resources (39.0.1-2) ...
Vormals nicht ausgewähltes Paket gyp wird gewählt.
Vorbereitung zum Entpacken von .../025-gyp_0.1+20150913git1f374df9-1ubuntu1_all.deb ...
Entpacken von gyp (0.1+20150913git1f374df9-1ubuntu1) ...
Vormals nicht ausgewähltes Paket javascript-common wird gewählt.
Vorbereitung zum Entpacken von .../026-javascript-common_11_all.deb ...
Entpacken von javascript-common (11) ...
Vormals nicht ausgewähltes Paket libalgorithm-diff-perl wird gewählt.
Vorbereitung zum Entpacken von .../027-libalgorithm-diff-perl_1.19.03-1_all.deb ...
Entpacken von libalgorithm-diff-perl (1.19.03-1) ...
Vormals nicht ausgewähltes Paket libalgorithm-diff-xs-perl wird gewählt.
Vorbereitung zum Entpacken von .../028-libalgorithm-diff-xs-perl_0.04-5_amd64.deb ...
Entpacken von libalgorithm-diff-xs-perl (0.04-5) ...
Vormals nicht ausgewähltes Paket libalgorithm-merge-perl wird gewählt.
Vorbereitung zum Entpacken von .../029-libalgorithm-merge-perl_0.08-3_all.deb ...
Entpacken von libalgorithm-merge-perl (0.08-3) ...
Vormals nicht ausgewähltes Paket libjs-async wird gewählt.
Vorbereitung zum Entpacken von .../030-libjs-async_0.8.0-3_all.deb ...
Entpacken von libjs-async (0.8.0-3) ...
Vormals nicht ausgewähltes Paket libjs-jquery wird gewählt.
Vorbereitung zum Entpacken von .../031-libjs-jquery_3.2.1-1_all.deb ...
Entpacken von libjs-jquery (3.2.1-1) ...
Vormals nicht ausgewähltes Paket libjs-node-uuid wird gewählt.
Vorbereitung zum Entpacken von .../032-libjs-node-uuid_1.4.7-5_all.deb ...
Entpacken von libjs-node-uuid (1.4.7-5) ...
Vormals nicht ausgewähltes Paket libjs-underscore wird gewählt.
Vorbereitung zum Entpacken von .../033-libjs-underscore_1.8.3~dfsg-1_all.deb ...
Entpacken von libjs-underscore (1.8.3~dfsg-1) ...
Vormals nicht ausgewähltes Paket libssl1.0-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../034-libssl1.0-dev_1.0.2n-1ubuntu5.1_amd64.deb ...
Entpacken von libssl1.0-dev:amd64 (1.0.2n-1ubuntu5.1) ...
Vormals nicht ausgewähltes Paket libuv1-dev:amd64 wird gewählt.
Vorbereitung zum Entpacken von .../035-libuv1-dev_1.18.0-3_amd64.deb ...
Entpacken von libuv1-dev:amd64 (1.18.0-3) ...
Vormals nicht ausgewähltes Paket manpages-dev wird gewählt.
Vorbereitung zum Entpacken von .../036-manpages-dev_4.15-1_all.deb ...
Entpacken von manpages-dev (4.15-1) ...
Vormals nicht ausgewähltes Paket node-async wird gewählt.
Vorbereitung zum Entpacken von .../037-node-async_0.8.0-3_all.deb ...
Entpacken von node-async (0.8.0-3) ...
Vormals nicht ausgewähltes Paket node-builtin-modules wird gewählt.
Vorbereitung zum Entpacken von .../038-node-builtin-modules_1.1.1-1_all.deb ...
Entpacken von node-builtin-modules (1.1.1-1) ...
Vormals nicht ausgewähltes Paket node-fs.realpath wird gewählt.
Vorbereitung zum Entpacken von .../039-node-fs.realpath_1.0.0-1_all.deb ...
Entpacken von node-fs.realpath (1.0.0-1) ...
Vormals nicht ausgewähltes Paket node-hosted-git-info wird gewählt.
Vorbereitung zum Entpacken von .../040-node-hosted-git-info_2.5.0-1_all.deb ...
Entpacken von node-hosted-git-info (2.5.0-1) ...
Vormals nicht ausgewähltes Paket node-wrappy wird gewählt.
Vorbereitung zum Entpacken von .../041-node-wrappy_1.0.2-1_all.deb ...
Entpacken von node-wrappy (1.0.2-1) ...
Vormals nicht ausgewähltes Paket node-once wird gewählt.
Vorbereitung zum Entpacken von .../042-node-once_1.4.0-2ubuntu1_all.deb ...
Entpacken von node-once (1.4.0-2ubuntu1) ...
Vormals nicht ausgewähltes Paket node-inflight wird gewählt.
Vorbereitung zum Entpacken von .../043-node-inflight_1.0.6-1_all.deb ...
Entpacken von node-inflight (1.0.6-1) ...
Vormals nicht ausgewähltes Paket node-is-builtin-module wird gewählt.
Vorbereitung zum Entpacken von .../044-node-is-builtin-module_1.0.0-1_all.deb ...
Entpacken von node-is-builtin-module (1.0.0-1) ...
Vormals nicht ausgewähltes Paket node-isexe wird gewählt.
Vorbereitung zum Entpacken von .../045-node-isexe_2.0.0-3_all.deb ...
Entpacken von node-isexe (2.0.0-3) ...
Vormals nicht ausgewähltes Paket node-node-uuid wird gewählt.
Vorbereitung zum Entpacken von .../046-node-node-uuid_1.4.7-5_all.deb ...
Entpacken von node-node-uuid (1.4.7-5) ...
Vormals nicht ausgewähltes Paket node-path-is-absolute wird gewählt.
Vorbereitung zum Entpacken von .../047-node-path-is-absolute_1.0.0-1_all.deb ...
Entpacken von node-path-is-absolute (1.0.0-1) ...
Vormals nicht ausgewähltes Paket node-pseudomap wird gewählt.
Vorbereitung zum Entpacken von .../048-node-pseudomap_1.0.2-1_all.deb ...
Entpacken von node-pseudomap (1.0.2-1) ...
Vormals nicht ausgewähltes Paket node-spdx-license-ids wird gewählt.
Vorbereitung zum Entpacken von .../049-node-spdx-license-ids_1.2.2-1_all.deb ...
Entpacken von node-spdx-license-ids (1.2.2-1) ...
Vormals nicht ausgewähltes Paket node-spdx-correct wird gewählt.
Vorbereitung zum Entpacken von .../050-node-spdx-correct_1.0.2-1_all.deb ...
Entpacken von node-spdx-correct (1.0.2-1) ...
Vormals nicht ausgewähltes Paket node-spdx-expression-parse wird gewählt.
Vorbereitung zum Entpacken von .../051-node-spdx-expression-parse_1.0.4-1_all.deb ...
Entpacken von node-spdx-expression-parse (1.0.4-1) ...
Vormals nicht ausgewähltes Paket node-underscore wird gewählt.
Vorbereitung zum Entpacken von .../052-node-underscore_1.8.3~dfsg-1_all.deb ...
Entpacken von node-underscore (1.8.3~dfsg-1) ...
Vormals nicht ausgewähltes Paket node-validate-npm-package-license wird gewählt.
Vorbereitung zum Entpacken von .../053-node-validate-npm-package-license_3.0.1-1_all.deb ...
Entpacken von node-validate-npm-package-license (3.0.1-1) ...
Vormals nicht ausgewähltes Paket node-yallist wird gewählt.
Vorbereitung zum Entpacken von .../054-node-yallist_2.0.0-1_all.deb ...
Entpacken von node-yallist (2.0.0-1) ...
Vormals nicht ausgewähltes Paket libjs-inherits wird gewählt.
Vorbereitung zum Entpacken von .../055-libjs-inherits_2.0.3-1_all.deb ...
Entpacken von libjs-inherits (2.0.3-1) ...
Vormals nicht ausgewähltes Paket node-abbrev wird gewählt.
Vorbereitung zum Entpacken von .../056-node-abbrev_1.0.9-1_all.deb ...
Entpacken von node-abbrev (1.0.9-1) ...
Vormals nicht ausgewähltes Paket node-ansi wird gewählt.
Vorbereitung zum Entpacken von .../057-node-ansi_0.3.0-2ubuntu1_all.deb ...
Entpacken von node-ansi (0.3.0-2ubuntu1) ...
Vormals nicht ausgewähltes Paket node-ansi-color-table wird gewählt.
Vorbereitung zum Entpacken von .../058-node-ansi-color-table_1.0.0-1_all.deb ...
Entpacken von node-ansi-color-table (1.0.0-1) ...
Vormals nicht ausgewähltes Paket node-archy wird gewählt.
Vorbereitung zum Entpacken von .../059-node-archy_1.0.0-1ubuntu1_all.deb ...
Entpacken von node-archy (1.0.0-1ubuntu1) ...
Vormals nicht ausgewähltes Paket node-balanced-match wird gewählt.
Vorbereitung zum Entpacken von .../060-node-balanced-match_0.4.2-1_all.deb ...
Entpacken von node-balanced-match (0.4.2-1) ...
Vormals nicht ausgewähltes Paket node-inherits wird gewählt.
Vorbereitung zum Entpacken von .../061-node-inherits_2.0.3-1_all.deb ...
Entpacken von node-inherits (2.0.3-1) ...
Vormals nicht ausgewähltes Paket node-block-stream wird gewählt.
Vorbereitung zum Entpacken von .../062-node-block-stream_0.0.9-1ubuntu1_all.deb ...
Entpacken von node-block-stream (0.0.9-1ubuntu1) ...
Vormals nicht ausgewähltes Paket node-concat-map wird gewählt.
Vorbereitung zum Entpacken von .../063-node-concat-map_0.0.1-1_all.deb ...
Entpacken von node-concat-map (0.0.1-1) ...
Vormals nicht ausgewähltes Paket node-brace-expansion wird gewählt.
Vorbereitung zum Entpacken von .../064-node-brace-expansion_1.1.8-1_all.deb ...
Entpacken von node-brace-expansion (1.1.8-1) ...
Vormals nicht ausgewähltes Paket node-delayed-stream wird gewählt.
Vorbereitung zum Entpacken von .../065-node-delayed-stream_0.0.5-1_all.deb ...
Entpacken von node-delayed-stream (0.0.5-1) ...
Vormals nicht ausgewähltes Paket node-combined-stream wird gewählt.
Vorbereitung zum Entpacken von .../066-node-combined-stream_0.0.5-1_all.deb ...
Entpacken von node-combined-stream (0.0.5-1) ...
Vormals nicht ausgewähltes Paket node-cookie-jar wird gewählt.
Vorbereitung zum Entpacken von .../067-node-cookie-jar_0.3.1-1_all.deb ...
Entpacken von node-cookie-jar (0.3.1-1) ...
Vormals nicht ausgewähltes Paket node-forever-agent wird gewählt.
Vorbereitung zum Entpacken von .../068-node-forever-agent_0.5.1-1_all.deb ...
Entpacken von node-forever-agent (0.5.1-1) ...
Vormals nicht ausgewähltes Paket node-mime wird gewählt.
Vorbereitung zum Entpacken von .../069-node-mime_1.3.4-1_all.deb ...
Entpacken von node-mime (1.3.4-1) ...
Vormals nicht ausgewähltes Paket node-form-data wird gewählt.
Vorbereitung zum Entpacken von .../070-node-form-data_0.1.0-1_all.deb ...
Entpacken von node-form-data (0.1.0-1) ...
Vormals nicht ausgewähltes Paket node-minimatch wird gewählt.
Vorbereitung zum Entpacken von .../071-node-minimatch_3.0.4-3_all.deb ...
Entpacken von node-minimatch (3.0.4-3) ...
Vormals nicht ausgewähltes Paket node-glob wird gewählt.
Vorbereitung zum Entpacken von .../072-node-glob_7.1.2-4_all.deb ...
Entpacken von node-glob (7.1.2-4) ...
Vormals nicht ausgewähltes Paket node-rimraf wird gewählt.
Vorbereitung zum Entpacken von .../073-node-rimraf_2.6.2-1_all.deb ...
Entpacken von node-rimraf (2.6.2-1) ...
Vormals nicht ausgewähltes Paket node-mkdirp wird gewählt.
Vorbereitung zum Entpacken von .../074-node-mkdirp_0.5.1-1_all.deb ...
Entpacken von node-mkdirp (0.5.1-1) ...
Vormals nicht ausgewähltes Paket node-graceful-fs wird gewählt.
Vorbereitung zum Entpacken von .../075-node-graceful-fs_4.1.11-1_all.deb ...
Entpacken von node-graceful-fs (4.1.11-1) ...
Vormals nicht ausgewähltes Paket node-fstream wird gewählt.
Vorbereitung zum Entpacken von .../076-node-fstream_1.0.10-1_all.deb ...
Entpacken von node-fstream (1.0.10-1) ...
Vormals nicht ausgewähltes Paket node-fstream-ignore wird gewählt.
Vorbereitung zum Entpacken von .../077-node-fstream-ignore_0.0.6-2_all.deb ...
Entpacken von node-fstream-ignore (0.0.6-2) ...
Vormals nicht ausgewähltes Paket node-github-url-from-git wird gewählt.
Vorbereitung zum Entpacken von .../078-node-github-url-from-git_1.4.0-1_all.deb ...
Entpacken von node-github-url-from-git (1.4.0-1) ...
Vormals nicht ausgewähltes Paket nodejs-dev wird gewählt.
Vorbereitung zum Entpacken von .../079-nodejs-dev_8.10.0~dfsg-2ubuntu0.3_amd64.deb ...
Entpacken von nodejs-dev (8.10.0~dfsg-2ubuntu0.3) ...
Vormals nicht ausgewähltes Paket node-nopt wird gewählt.
Vorbereitung zum Entpacken von .../080-node-nopt_3.0.6-3_all.deb ...
Entpacken von node-nopt (3.0.6-3) ...
Vormals nicht ausgewähltes Paket node-npmlog wird gewählt.
Vorbereitung zum Entpacken von .../081-node-npmlog_0.0.4-1_all.deb ...
Entpacken von node-npmlog (0.0.4-1) ...
Vormals nicht ausgewähltes Paket node-osenv wird gewählt.
Vorbereitung zum Entpacken von .../082-node-osenv_0.1.4-1_all.deb ...
Entpacken von node-osenv (0.1.4-1) ...
Vormals nicht ausgewähltes Paket node-tunnel-agent wird gewählt.
Vorbereitung zum Entpacken von .../083-node-tunnel-agent_0.3.1-1_all.deb ...
Entpacken von node-tunnel-agent (0.3.1-1) ...
Vormals nicht ausgewähltes Paket node-json-stringify-safe wird gewählt.
Vorbereitung zum Entpacken von .../084-node-json-stringify-safe_5.0.0-1_all.deb ...
Entpacken von node-json-stringify-safe (5.0.0-1) ...
Vormals nicht ausgewähltes Paket node-qs wird gewählt.
Vorbereitung zum Entpacken von .../085-node-qs_2.2.4-1ubuntu1_all.deb ...
Entpacken von node-qs (2.2.4-1ubuntu1) ...
Vormals nicht ausgewähltes Paket node-request wird gewählt.
Vorbereitung zum Entpacken von .../086-node-request_2.26.1-1_all.deb ...
Entpacken von node-request (2.26.1-1) ...
Vormals nicht ausgewähltes Paket node-semver wird gewählt.
Vorbereitung zum Entpacken von .../087-node-semver_5.4.1-1_all.deb ...
Entpacken von node-semver (5.4.1-1) ...
Vormals nicht ausgewähltes Paket node-tar wird gewählt.
Vorbereitung zum Entpacken von .../088-node-tar_2.2.1-1_all.deb ...
Entpacken von node-tar (2.2.1-1) ...
Vormals nicht ausgewähltes Paket node-which wird gewählt.
Vorbereitung zum Entpacken von .../089-node-which_1.3.0-1_all.deb ...
Entpacken von node-which (1.3.0-1) ...
Vormals nicht ausgewähltes Paket node-gyp wird gewählt.
Vorbereitung zum Entpacken von .../090-node-gyp_3.6.2-1ubuntu1_all.deb ...
Entpacken von node-gyp (3.6.2-1ubuntu1) ...
Vormals nicht ausgewähltes Paket node-ini wird gewählt.
Vorbereitung zum Entpacken von .../091-node-ini_1.3.4-1_all.deb ...
Entpacken von node-ini (1.3.4-1) ...
Vormals nicht ausgewähltes Paket node-lockfile wird gewählt.
Vorbereitung zum Entpacken von .../092-node-lockfile_0.4.1-1_all.deb ...
Entpacken von node-lockfile (0.4.1-1) ...
Vormals nicht ausgewähltes Paket node-lru-cache wird gewählt.
Vorbereitung zum Entpacken von .../093-node-lru-cache_4.1.1-1_all.deb ...
Entpacken von node-lru-cache (4.1.1-1) ...
Vormals nicht ausgewähltes Paket node-mute-stream wird gewählt.
Vorbereitung zum Entpacken von .../094-node-mute-stream_0.0.7-1_all.deb ...
Entpacken von node-mute-stream (0.0.7-1) ...
Vormals nicht ausgewähltes Paket node-normalize-package-data wird gewählt.
Vorbereitung zum Entpacken von .../095-node-normalize-package-data_2.3.5-2_all.deb ...
Entpacken von node-normalize-package-data (2.3.5-2) ...
Vormals nicht ausgewähltes Paket node-read wird gewählt.
Vorbereitung zum Entpacken von .../096-node-read_1.0.7-1_all.deb ...
Entpacken von node-read (1.0.7-1) ...
Vormals nicht ausgewähltes Paket node-read-package-json wird gewählt.
Vorbereitung zum Entpacken von .../097-node-read-package-json_1.2.4-1_all.deb ...
Entpacken von node-read-package-json (1.2.4-1) ...
Vormals nicht ausgewähltes Paket node-retry wird gewählt.
Vorbereitung zum Entpacken von .../098-node-retry_0.10.1-1_all.deb ...
Entpacken von node-retry (0.10.1-1) ...
Vormals nicht ausgewähltes Paket node-sha wird gewählt.
Vorbereitung zum Entpacken von .../099-node-sha_1.2.3-1_all.deb ...
Entpacken von node-sha (1.2.3-1) ...
Vormals nicht ausgewähltes Paket node-slide wird gewählt.
Vorbereitung zum Entpacken von .../100-node-slide_1.1.6-1_all.deb ...
Entpacken von node-slide (1.1.6-1) ...
Vormals nicht ausgewähltes Paket npm wird gewählt.
Vorbereitung zum Entpacken von .../101-npm_3.5.2-0ubuntu4_all.deb ...
Entpacken von npm (3.5.2-0ubuntu4) ...
libquadmath0:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
node-lockfile (0.4.1-1) wird eingerichtet ...
node-spdx-expression-parse (1.0.4-1) wird eingerichtet ...
libjs-jquery (3.2.1-1) wird eingerichtet ...
libatomic1:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
node-qs (2.2.4-1ubuntu1) wird eingerichtet ...
node-osenv (0.1.4-1) wird eingerichtet ...
node-ansi (0.3.0-2ubuntu1) wird eingerichtet ...
make (4.1-9.1ubuntu1) wird eingerichtet ...
libjs-node-uuid (1.4.7-5) wird eingerichtet ...
node-hosted-git-info (2.5.0-1) wird eingerichtet ...
libjs-underscore (1.8.3~dfsg-1) wird eingerichtet ...
node-delayed-stream (0.0.5-1) wird eingerichtet ...
Trigger für mime-support (3.60ubuntu1) werden verarbeitet ...
libasan4:amd64 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
Trigger für desktop-file-utils (0.23-1ubuntu3.18.04.1) werden verarbeitet ...
libjs-inherits (2.0.3-1) wird eingerichtet ...
node-tunnel-agent (0.3.1-1) wird eingerichtet ...
node-balanced-match (0.4.2-1) wird eingerichtet ...
libcilkrts5:amd64 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
node-node-uuid (1.4.7-5) wird eingerichtet ...
node-yallist (2.0.0-1) wird eingerichtet ...
libubsan0:amd64 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
node-slide (1.1.6-1) wird eingerichtet ...
libtsan0:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
node-github-url-from-git (1.4.0-1) wird eingerichtet ...
node-pseudomap (1.0.2-1) wird eingerichtet ...
linux-libc-dev:amd64 (4.15.0-36.39) wird eingerichtet ...
python2.7 (2.7.15~rc1-1) wird eingerichtet ...
libssl1.0-dev:amd64 (1.0.2n-1ubuntu5.1) wird eingerichtet ...
node-spdx-license-ids (1.2.2-1) wird eingerichtet ...
node-combined-stream (0.0.5-1) wird eingerichtet ...
node-wrappy (1.0.2-1) wird eingerichtet ...
node-mime (1.3.4-1) wird eingerichtet ...
node-abbrev (1.0.9-1) wird eingerichtet ...
node-semver (5.4.1-1) wird eingerichtet ...
liblsan0:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
node-retry (0.10.1-1) wird eingerichtet ...
libpython-stdlib:amd64 (2.7.15~rc1-1) wird eingerichtet ...
libmpx2:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
node-forever-agent (0.5.1-1) wird eingerichtet ...
node-underscore (1.8.3~dfsg-1) wird eingerichtet ...
dpkg-dev (1.19.0.5ubuntu2) wird eingerichtet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
node-json-stringify-safe (5.0.0-1) wird eingerichtet ...
node-inherits (2.0.3-1) wird eingerichtet ...
libfakeroot:amd64 (1.22-2ubuntu1) wird eingerichtet ...
node-graceful-fs (4.1.11-1) wird eingerichtet ...
node-archy (1.0.0-1ubuntu1) wird eingerichtet ...
libalgorithm-diff-perl (1.19.03-1) wird eingerichtet ...
node-path-is-absolute (1.0.0-1) wird eingerichtet ...
node-builtin-modules (1.1.1-1) wird eingerichtet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
node-isexe (2.0.0-3) wird eingerichtet ...
node-spdx-correct (1.0.2-1) wird eingerichtet ...
libc-dev-bin (2.27-3ubuntu1) wird eingerichtet ...
Trigger für gnome-menus (3.13.3-11ubuntu1.1) werden verarbeitet ...
javascript-common (11) wird eingerichtet ...
apache2_invoke: Enable configuration javascript-common
node-cookie-jar (0.3.1-1) wird eingerichtet ...
node-mute-stream (0.0.7-1) wird eingerichtet ...
libjs-async (0.8.0-3) wird eingerichtet ...
manpages-dev (4.15-1) wird eingerichtet ...
libc6-dev:amd64 (2.27-3ubuntu1) wird eingerichtet ...
node-concat-map (0.0.1-1) wird eingerichtet ...
node-ini (1.3.4-1) wird eingerichtet ...
node-mkdirp (0.5.1-1) wird eingerichtet ...
node-once (1.4.0-2ubuntu1) wird eingerichtet ...
libitm1:amd64 (8.2.0-1ubuntu2~18.04) wird eingerichtet ...
python (2.7.15~rc1-1) wird eingerichtet ...
node-sha (1.2.3-1) wird eingerichtet ...
node-fs.realpath (1.0.0-1) wird eingerichtet ...
libuv1-dev:amd64 (1.18.0-3) wird eingerichtet ...
node-brace-expansion (1.1.8-1) wird eingerichtet ...
node-ansi-color-table (1.0.0-1) wird eingerichtet ...
node-npmlog (0.0.4-1) wird eingerichtet ...
node-is-builtin-module (1.0.0-1) wird eingerichtet ...
node-nopt (3.0.6-3) wird eingerichtet ...
node-which (1.3.0-1) wird eingerichtet ...
node-lru-cache (4.1.1-1) wird eingerichtet ...
node-block-stream (0.0.9-1ubuntu1) wird eingerichtet ...
python-pkg-resources (39.0.1-2) wird eingerichtet ...
fakeroot (1.22-2ubuntu1) wird eingerichtet ...
update-alternatives: /usr/bin/fakeroot-sysv wird verwendet, um /usr/bin/fakeroot (fakeroot) im automatischen Modus bereitzustellen
libgcc-7-dev:amd64 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
node-validate-npm-package-license (3.0.1-1) wird eingerichtet ...
node-inflight (1.0.6-1) wird eingerichtet ...
libstdc++-7-dev:amd64 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
libalgorithm-merge-perl (0.08-3) wird eingerichtet ...
node-read (1.0.7-1) wird eingerichtet ...
libalgorithm-diff-xs-perl (0.04-5) wird eingerichtet ...
gyp (0.1+20150913git1f374df9-1ubuntu1) wird eingerichtet ...
node-async (0.8.0-3) wird eingerichtet ...
node-form-data (0.1.0-1) wird eingerichtet ...
node-request (2.26.1-1) wird eingerichtet ...
node-minimatch (3.0.4-3) wird eingerichtet ...
nodejs-dev (8.10.0~dfsg-2ubuntu0.3) wird eingerichtet ...
node-normalize-package-data (2.3.5-2) wird eingerichtet ...
gcc-7 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
g++-7 (7.3.0-27ubuntu1~18.04) wird eingerichtet ...
gcc (4:7.3.0-3ubuntu2.1) wird eingerichtet ...
node-glob (7.1.2-4) wird eingerichtet ...
g++ (4:7.3.0-3ubuntu2.1) wird eingerichtet ...
update-alternatives: /usr/bin/g++ wird verwendet, um /usr/bin/c++ (c++) im automatischen Modus bereitzustellen
build-essential (12.4ubuntu1) wird eingerichtet ...
node-rimraf (2.6.2-1) wird eingerichtet ...
node-read-package-json (1.2.4-1) wird eingerichtet ...
node-fstream (1.0.10-1) wird eingerichtet ...
node-fstream-ignore (0.0.6-2) wird eingerichtet ...
node-tar (2.2.1-1) wird eingerichtet ...
node-gyp (3.6.2-1ubuntu1) wird eingerichtet ...
npm (3.5.2-0ubuntu4) wird eingerichtet ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
```

Nun kann ich Sie Module und Pakete für die Verwendung mit Node.js installieren.

Aufgrund eines Konflikts mit einem anderen Paket heißt die ausführbare 
Datei aus den Ubuntu-Repositories `nodejs` anstelle von `node`. 

Um zu prüfen, welche Version von `Node.js` beziehungseise `npm` ich 
installiert habe, verwende ich folgende Befehle.

```
astrid@astrid-TravelMate-5760G:~$ nodejs -v
v8.10.0
```


```
astrid@astrid-TravelMate-5760G:~$ npm -v
3.5.2
```

Um eine neuere Version von `Node.js` zu erhalten, kann ich das von NodeSource 
verwaltete PPA (persönliches Paketarchiv) hinzufügen. 
Dieses beinhaltet aktuellere Versionen von Node.js als die 
offiziellen Ubuntu-Repositories. 
Ich installiere zuerst das PPA, um auf seine Inhalte zuzugreifen. 
Ich Verwende `curl`, um das Installationsskript für Ihre bevorzugte Version abzurufen. 

Als erstes wechele ich in mein Homeverzeichnis

```
astrid@astrid-TravelMate-5760G:~$ cd ~
astrid@astrid-TravelMate-5760G:~$ curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh
```

Ich kann den Inhalt dieses Skripts mit `gedit` überprüfen:

```
astrid@astrid-TravelMate-5760G:~$ gedit nodesource_setup.sh 
```

Ich führe das Skript mit dem Befehl `sudo bash nodesource_setup.sh` aus.

```
astrid@astrid-TravelMate-5760G:~$ sudo bash nodesource_setup.sh
[sudo] Passwort für astrid: 

## Installing the NodeSource Node.js 10.x repo...

## Populating apt-get cache...

+ apt-get update
OK:1 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease
Holen:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
OK:3 http://de.archive.ubuntu.com/ubuntu bionic InRelease                      
OK:4 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease              
OK:5 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease
OK:6 https://deb.nodesource.com/node_8.x bionic InRelease
Es wurden 83,2 kB in 1 s geholt (65,9 kB/s).
Paketlisten werden gelesen... Fertig

## Confirming "bionic" is supported...

+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_10.x/dists/bionic/Release'

## Adding the NodeSource signing key to your keyring...

+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
OK

## Creating apt sources list file for the NodeSource Node.js 10.x repo...

+ echo 'deb https://deb.nodesource.com/node_10.x bionic main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src https://deb.nodesource.com/node_10.x bionic main' >> /etc/apt/sources.list.d/nodesource.list

## Running `apt-get update` for you...

+ apt-get update
OK:1 http://de.archive.ubuntu.com/ubuntu bionic InRelease
OK:2 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease         
OK:3 http://de.archive.ubuntu.com/ubuntu bionic-updates InRelease              
Holen:4 https://deb.nodesource.com/node_10.x bionic InRelease [4.611 B]        
OK:5 http://de.archive.ubuntu.com/ubuntu bionic-backports InRelease            
Holen:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
Holen:7 https://deb.nodesource.com/node_10.x bionic/main amd64 Packages [768 B]
Es wurden 88,6 kB in 1 s geholt (94,7 kB/s).               
Paketlisten werden gelesen... Fertig

## Run `sudo apt-get install -y nodejs` to install Node.js 10.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn
```

Der PPA wird zu meiner Konfiguration hinzugefügt und mein lokaler Paket-Cache 
wird automatisch aktualisiert. 
Nachdem ich das Setup-Skript von Nodesource ausgeführt haben, kann ich das Node.js-Paket 
auf die gleiche Weise wie oben installieren.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install nodejs
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden aktualisiert (Upgrade):
  nodejs
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 15,0 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 7.648 kB Plattenplatz zusätzlich benutzt.
Holen:1 https://deb.nodesource.com/node_10.x bionic/main amd64 nodejs amd64 10.12.0-1nodesource1 [15,0 MB]
Es wurden 15,0 MB in 4 s geholt (4.249 kB/s).
(Lese Datenbank ... 175104 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../nodejs_10.12.0-1nodesource1_amd64.deb ...
Detected old npm client, removing...
Entpacken von nodejs (10.12.0-1nodesource1) über (8.12.0-1nodesource1) ...
nodejs (10.12.0-1nodesource1) wird eingerichtet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
```

Nun ist meine installierte Version aktueller und ausreichend für die Arbeit mit Joomla!.

```
astrid@astrid-TravelMate-5760G:~$ nodejs -v
v10.12.0
astrid@astrid-TravelMate-5760G:~$ npm -v
6.4.1
```

Damit alle npm-Pakete funktionieren muss ich das build-essential-Paket noch installieren.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt install build-essential 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
build-essential ist schon die neueste Version (12.4ubuntu1).
build-essential wurde als manuell installiert festgelegt.
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  gyp javascript-common libc-ares2 libhttp-parser2.7.1 libjs-async
  libjs-inherits libjs-jquery libjs-node-uuid libjs-underscore libssl1.0-dev
  libuv1 libuv1-dev node-abbrev node-ansi node-ansi-color-table node-archy
  node-async node-balanced-match node-block-stream node-brace-expansion
  node-builtin-modules node-combined-stream node-concat-map node-cookie-jar
  node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob
  node-graceful-fs node-gyp node-hosted-git-info node-inflight node-inherits
  node-ini node-is-builtin-module node-isexe node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-path-is-absolute node-pseudomap
  node-qs node-read node-read-package-json node-request node-retry node-rimraf
  node-semver node-sha node-slide node-spdx-correct node-spdx-expression-parse
  node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist
  nodejs-doc python-pkg-resources
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 11 nicht aktualisiert.
```

Jetzt habe ich die notwendigen Werkzeuge, um mit npm-Paketen zu arbeiten, 
die das Kompilieren von Joomla-Quellcode erfordern. 
Weil es mir am Ende des letzten Befehls empfohlen wurde, führe ich noch den Befehl 
`sudo apt autoremove` aus.

```
astrid@astrid-TravelMate-5760G:~$ sudo apt autoremove
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  gyp javascript-common libc-ares2 libhttp-parser2.7.1 libjs-async
  libjs-inherits libjs-jquery libjs-node-uuid libjs-underscore libssl1.0-dev
  libuv1 libuv1-dev node-abbrev node-ansi node-ansi-color-table node-archy
  node-async node-balanced-match node-block-stream node-brace-expansion
  node-builtin-modules node-combined-stream node-concat-map node-cookie-jar
  node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob
  node-graceful-fs node-gyp node-hosted-git-info node-inflight node-inherits
  node-ini node-is-builtin-module node-isexe node-json-stringify-safe
  node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data
  node-npmlog node-once node-osenv node-path-is-absolute node-pseudomap
  node-qs node-read node-read-package-json node-request node-retry node-rimraf
  node-semver node-sha node-slide node-spdx-correct node-spdx-expression-parse
  node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist
  nodejs-doc python-pkg-resources
0 aktualisiert, 0 neu installiert, 76 zu entfernen und 11 nicht aktualisiert.
Nach dieser Operation werden 19,1 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] J
(Lese Datenbank ... 175935 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von node-gyp (3.6.2-1ubuntu1) ...
Entfernen von gyp (0.1+20150913git1f374df9-1ubuntu1) ...
Entfernen von javascript-common (11) ...
Conf javascript-common disabled.
apache2_invoke prerm: Disable configuration javascript-common
Entfernen von libc-ares2:amd64 (1.14.0-1) ...
Entfernen von libhttp-parser2.7.1:amd64 (2.7.1-2) ...
Entfernen von node-request (2.26.1-1) ...
Entfernen von node-form-data (0.1.0-1) ...
Entfernen von node-async (0.8.0-3) ...
Entfernen von libjs-async (0.8.0-3) ...
Entfernen von node-tar (2.2.1-1) ...
Entfernen von node-fstream-ignore (0.0.6-2) ...
Entfernen von node-fstream (1.0.10-1) ...
Entfernen von node-rimraf (2.6.2-1) ...
Entfernen von libjs-jquery (3.2.1-1) ...
Entfernen von node-node-uuid (1.4.7-5) ...
Entfernen von libjs-node-uuid (1.4.7-5) ...
Entfernen von node-underscore (1.8.3~dfsg-1) ...
Entfernen von libjs-underscore (1.8.3~dfsg-1) ...
Entfernen von libssl1.0-dev:amd64 (1.0.2n-1ubuntu5.1) ...
Entfernen von libuv1-dev:amd64 (1.18.0-3) ...
Entfernen von libuv1:amd64 (1.18.0-3) ...
Entfernen von node-nopt (3.0.6-3) ...
Entfernen von node-abbrev (1.0.9-1) ...
Entfernen von node-ansi-color-table (1.0.0-1) ...
Entfernen von node-npmlog (0.0.4-1) ...
Entfernen von node-ansi (0.3.0-2ubuntu1) ...
Entfernen von node-archy (1.0.0-1ubuntu1) ...
Entfernen von node-block-stream (0.0.9-1ubuntu1) ...
Entfernen von node-read-package-json (1.2.4-1) ...
Entfernen von node-normalize-package-data (2.3.5-2) ...
Entfernen von node-is-builtin-module (1.0.0-1) ...
Entfernen von node-builtin-modules (1.1.1-1) ...
Entfernen von node-combined-stream (0.0.5-1) ...
Entfernen von node-cookie-jar (0.3.1-1) ...
Entfernen von node-delayed-stream (0.0.5-1) ...
Entfernen von node-forever-agent (0.5.1-1) ...
Entfernen von node-github-url-from-git (1.4.0-1) ...
Entfernen von node-graceful-fs (4.1.11-1) ...
Entfernen von node-hosted-git-info (2.5.0-1) ...
Entfernen von node-ini (1.3.4-1) ...
Entfernen von node-which (1.3.0-1) ...
Entfernen von node-isexe (2.0.0-3) ...
Entfernen von node-json-stringify-safe (5.0.0-1) ...
Entfernen von node-lockfile (0.4.1-1) ...
Entfernen von node-lru-cache (4.1.1-1) ...
Entfernen von node-mime (1.3.4-1) ...
Entfernen von node-mkdirp (0.5.1-1) ...
Entfernen von node-read (1.0.7-1) ...
Entfernen von node-mute-stream (0.0.7-1) ...
Entfernen von node-osenv (0.1.4-1) ...
Entfernen von node-pseudomap (1.0.2-1) ...
Entfernen von node-qs (2.2.4-1ubuntu1) ...
Entfernen von node-retry (0.10.1-1) ...
Entfernen von node-semver (5.4.1-1) ...
Entfernen von node-sha (1.2.3-1) ...
Entfernen von node-slide (1.1.6-1) ...
Entfernen von node-validate-npm-package-license (3.0.1-1) ...
Entfernen von node-spdx-correct (1.0.2-1) ...
Entfernen von node-spdx-expression-parse (1.0.4-1) ...
Entfernen von node-spdx-license-ids (1.2.2-1) ...
Entfernen von node-tunnel-agent (0.3.1-1) ...
Entfernen von node-yallist (2.0.0-1) ...
Entfernen von nodejs-doc (8.10.0~dfsg-2ubuntu0.3) ...
Entfernen von python-pkg-resources (39.0.1-2) ...
Entfernen von node-glob (7.1.2-4) ...
Entfernen von node-inherits (2.0.3-1) ...
Entfernen von libjs-inherits (2.0.3-1) ...
Entfernen von node-minimatch (3.0.4-3) ...
Entfernen von node-brace-expansion (1.1.8-1) ...
Entfernen von node-balanced-match (0.4.2-1) ...
Entfernen von node-concat-map (0.0.1-1) ...
Entfernen von node-fs.realpath (1.0.0-1) ...
Entfernen von node-inflight (1.0.6-1) ...
Entfernen von node-once (1.4.0-2ubuntu1) ...
Entfernen von node-path-is-absolute (1.0.0-1) ...
Entfernen von node-wrappy (1.0.2-1) ...
Trigger für libc-bin (2.27-3ubuntu1) werden verarbeitet ...
Trigger für man-db (2.8.3-2) werden verarbeitet ...
```

### Letzte Schritt für Joomla 4

Als erstes stelle ich sicher, dass ich mich immer noch 
im richtigen Verzeichnis und auf dem richtigen 
Zweig befinde.

```
astrid@astrid-TravelMate-5760G:~$ cd /var/www/html/joomla-cms/
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ git branch
* 4.0-dev
  staging
```

Mit den hier in den vorherigen Kapiteln beschriebenen Installationen klappt es nun 
mit `composer install` und `npm install`.


```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ composer install
Loading composer repositories with package information
Installing dependencies (including require-dev) from lock file
Package operations: 123 installs, 0 updates, 0 removals
  - Installing paragonie/random_compat (v9.99.99): Loading from cache
  - Installing defuse/php-encryption (v2.2.1): Downloading (100%)         
  - Installing doctrine/inflector (v1.2.0): Downloading (100%)         
  - Installing google/recaptcha (1.2.1): Downloading (100%)         
  - Installing psr/http-message (1.0.1): Loading from cache
  - Installing zendframework/zend-diactoros (1.8.6):Downloading (100%)         )
  - Installing psr/log (1.0.2): Downloading (100%)         
  - Installing joomla/string (dev-2.0-dev d63a76e): Downloading (100%)         
  - Installing joomla/utilities (dev-2.0-dev 1774547): Downloading (connecting..Downloading (100%)         
  - Installing joomla/registry (dev-2.0-dev f7386bf): Downloading (connecting...Downloading (100%)         
  - Installing joomla/filter (1.3.5): Downloading (100%)         
  - Installing joomla/input (1.3.0): Downloading (100%)         
  - Installing joomla/event (dev-2.0-dev ba75ff8): Downloading (100%)         
  - Installing joomla/application (dev-2.0-dev bfc34f7): Downloading (connectingDownloading (100%)         
  - Installing joomla/filesystem (1.4.0): Downloading (100%)         
  - Installing joomla/archive (1.1.5): Downloading (100%)         
  - Installing joomla/authentication (dev-2.0-dev e587d3b): Downloading (connectDownloading (100%)         
  - Installing symfony/polyfill-mbstring (v1.9.0): Loading from cache
  - Installing symfony/debug (v3.4.16): Downloading (100%)         
  - Installing symfony/console (v3.4.16): Downloading (100%)         
  - Installing joomla/console (dev-master 026a701): Downloading (100%)         
  - Installing joomla/controller (dev-2.0-dev 45fab25): Downloading (connecting.Downloading (100%)         
  - Installing joomla/crypt (dev-master 8c1c1ee): Downloading (100%)         
  - Installing joomla/data (dev-2.0-dev dd06e7d): Downloading (100%)         
  - Installing joomla/database (dev-2.0-dev 414bbd6): Downloading (connecting...Downloading (100%)         
  - Installing psr/container (1.0.0): Loading from cache
  - Installing joomla/di (dev-2.0-dev 1928839): Downloading (100%)         
  - Installing joomla/uri (dev-2.0-dev b051dac): Downloading (100%)         
  - Installing composer/ca-bundle (1.1.2): Downloading (100%)         
  - Installing joomla/http (dev-2.0-dev 7d5857d): Downloading (100%)         
  - Installing joomla/image (dev-2.0-dev 0222c4a): Downloading (100%)         
  - Installing joomla/ldap (dev-2.0-dev f19a37a): Downloading (100%)         
  - Installing joomla/session (dev-2.0-dev b219e59):Downloading (100%)         )
  - Installing joomla/oauth1 (dev-2.0-dev 0efbdbe): Downloading (100%)         
  - Installing joomla/oauth2 (dev-2.0-dev 2034b82): Downloading (100%)         
  - Installing symfony/var-dumper (v3.4.16): Downloading (100%)         
  - Installing maximebf/debugbar (v1.15.0): Downloading (100%)         
  - Installing mso/idna-convert (v1.1.0): Downloading (100%)         
  - Installing paragonie/sodium_compat (v1.7.0): Downloading (100%)         
  - Installing phpmailer/phpmailer (v6.0.5): Downloading (100%)         
  - Installing symfony/polyfill-util (v1.9.0): Downloading (100%)         
  - Installing symfony/polyfill-php56 (v1.9.0): Downloading (100%)         
  - Installing symfony/options-resolver (v3.4.16): Downloading (100%)         
  - Installing symfony/ldap (v3.4.16): Downloading (100%)         
  - Installing psr/link (1.0.0): Downloading (100%)         
  - Installing fig/link-util (1.0.0): Downloading (100%)         
  - Installing symfony/web-link (v3.4.16): Downloading (100%)         
  - Installing wamania/php-stemmer (1.2): Downloading (100%)         
  - Installing behat/gherkin (v4.5.1): Downloading (100%)         
  - Installing sebastian/diff (2.0.1): Downloading (100%)         
  - Installing sebastian/recursion-context (3.0.0): Downloading (100%)         
  - Installing sebastian/exporter (3.1.0): Downloading (100%)         
  - Installing sebastian/comparator (2.1.3): Downloading (100%)         
  - Installing sebastian/version (2.0.1): Downloading (100%)         
  - Installing sebastian/resource-operations (1.0.0): Downloading (connecting...Downloading (100%)         
  - Installing sebastian/object-reflector (1.1.1): Downloading (100%)         
  - Installing sebastian/object-enumerator (3.0.3): Downloading (100%)         
  - Installing sebastian/global-state (2.0.0): Downloading (100%)         
  - Installing sebastian/environment (3.1.0): Downloading (100%)         
  - Installing phpunit/php-text-template (1.2.1): Loading from cache
  - Installing doctrine/instantiator (1.0.5): Loading from cache
  - Installing phpunit/phpunit-mock-objects (5.0.10): Downloading (connecting...Downloading (100%)         
  - Installing phpunit/php-timer (1.0.9): Loading from cache
  - Installing phpunit/php-file-iterator (1.4.5): Loading from cache
  - Installing theseer/tokenizer (1.1.0): Downloading (100%)         
  - Installing sebastian/code-unit-reverse-lookup (1.0.1): Downloading (connectiDownloading (100%)         
  - Installing phpunit/php-token-stream (2.0.2): Downloading (100%)         
  - Installing phpunit/php-code-coverage (5.3.2): Downloading (100%)         
  - Installing webmozart/assert (1.3.0): Downloading (100%)         
  - Installing phpdocumentor/reflection-common (1.0.1): Downloading (connecting.Downloading (100%)         
  - Installing phpdocumentor/type-resolver (0.4.0): Downloading (100%)         
  - Installing phpdocumentor/reflection-docblock (4.3.0): Downloading (connectinDownloading (100%)         
  - Installing phpspec/prophecy (1.8.0): Loading from cache
  - Installing phar-io/version (1.0.1): Downloading (100%)         
  - Installing phar-io/manifest (1.0.1): Downloading (100%)         
  - Installing myclabs/deep-copy (1.7.0): Downloading (100%)         
  - Installing phpunit/phpunit (6.5.13): Downloading (100%)         
  - Installing codeception/phpunit-wrapper (6.0.12):Downloading (100%)         )
  - Installing codeception/stub (2.0.4): Downloading (100%)         
  - Installing symfony/finder (v3.4.16): Downloading (100%)         
  - Installing symfony/event-dispatcher (v3.4.16): Loading from cache
  - Installing consolidation/output-formatters (3.2.1): Downloading (connecting.Downloading (100%)         
  - Installing consolidation/annotated-command (2.9.1): Downloading (connecting.Downloading (100%)         
  - Installing dflydev/dot-access-data (v1.1.0): Downloading (100%)         
  - Installing grasmash/expander (1.0.0): Downloading (100%)         
  - Installing consolidation/config (1.1.0): Downloading (100%)         
  - Installing consolidation/log (1.0.6): Downloading (100%)         
  - Installing symfony/polyfill-ctype (v1.9.0): Loading from cache
  - Installing symfony/filesystem (v3.4.16): Downloading (100%)         
  - Installing consolidation/self-update (1.1.3): Downloading (100%)         
  - Installing doctrine/lexer (v1.0.1): Downloading (100%)         
  - Installing symfony/process (v3.4.16): Downloading (100%)         
  - Installing facebook/webdriver (1.6.0): Downloading (100%)         
  - Installing symfony/stopwatch (v3.4.16): Downloading (100%)         
  - Installing symfony/polyfill-php72 (v1.9.0): Downloading (100%)         
  - Installing symfony/polyfill-php70 (v1.9.0): Downloading (100%)         
  - Installing php-cs-fixer/diff (v1.3.0): Downloading (100%)         
  - Installing doctrine/annotations (v1.4.0): Downloading (100%)         
  - Installing composer/xdebug-handler (1.3.0): Downloading (100%)         
  - Installing composer/semver (1.4.2): Downloading (100%)         
  - Installing friendsofphp/php-cs-fixer (v2.13.0): Downloading (100%)         
  - Installing g1a/composer-test-scenarios (2.2.0): Downloading (100%)         
  - Installing symfony/yaml (v3.4.16): Downloading (100%)         
  - Installing grasmash/yaml-expander (1.4.0): Downloading (100%)         
  - Installing guzzlehttp/psr7 (1.4.2): Downloading (100%)         
  - Installing guzzlehttp/promises (v1.3.1): Downloading (100%)         
  - Installing guzzlehttp/guzzle (6.3.3): Downloading (100%)         
  - Installing container-interop/container-interop (1.2.0): Loading from cache
  - Installing league/container (2.4.1): Downloading (100%)         
  - Installing consolidation/robo (1.3.1): Downloading (100%)         
  - Installing joomla-projects/robo-joomla (dev-develop f2afed9): Cloning f2afed9231 from cache
  - Installing joomla/mediawiki (dev-master d2e40c7): Downloading (connecting...Downloading (100%)         
  - Installing joomla-projects/selenium-server-standalone (v3.14.0): DownloadingDownloading (100%)         
  - Installing joomla-projects/joomla-browser (v4.0.0.x-dev a8fb79d): Cloning a8fb79ddbd from cache
  - Installing symfony/dom-crawler (v3.4.16): Downloading (100%)         
  - Installing symfony/css-selector (v3.4.16): Downloading (100%)         
  - Installing symfony/browser-kit (v3.4.16): Downloading (100%)         
  - Installing codeception/codeception (2.5.0): Downloading (100%)         
  - Installing joomla/test-system (dev-4.0-dev 6c8be15): Cloning 6c8be15303 from cache
  - Installing joomla/test-unit (dev-4.0-dev 08a1c36): Cloning 08a1c3668e from cache
  - Installing phpunit/dbunit (3.0.3): Downloading (100%)         
  - Installing phpunit/phpunit-dom-assertions (v2.0.1): Downloading (connecting.Downloading (100%)         
  - Installing squizlabs/php_codesniffer (1.5.6): Loading from cache
paragonie/random_compat suggests installing ext-libsodium (Provides a modern crypto API that can be used to generate random bytes.)
joomla/filter suggests installing joomla/language (Required only if you want to use `OutputFilter::stringURLSafe`.)
joomla/application suggests installing joomla/router (To use WebApplication or ControllerResolverInterface implementations, install joomla/router)
joomla/archive suggests installing ext-bz2 (To extract bzip2 compressed packages)
symfony/console suggests installing psr/log-implementation (For using the console logger)
symfony/console suggests installing symfony/lock
joomla/database suggests installing ext-pgsql (To connect to a PostgreSQL database)
joomla/database suggests installing ext-sqlsrv (To connect to a SQL Server database)
joomla/session suggests installing ext-apcu (To use APCu cache as a session handler)
joomla/session suggests installing ext-memcached (To use a Memcached server as a session handler)
joomla/session suggests installing ext-redis (To use a Redis server as a session handler)
joomla/session suggests installing ext-wincache (To use WinCache as a session handler)
symfony/var-dumper suggests installing ext-intl (To show region name in time zone dump)
symfony/var-dumper suggests installing ext-symfony_debug
maximebf/debugbar suggests installing kriswallsmith/assetic (The best way to manage assets)
maximebf/debugbar suggests installing monolog/monolog (Log using Monolog)
maximebf/debugbar suggests installing predis/predis (Redis storage)
paragonie/sodium_compat suggests installing ext-libsodium (PHP < 7.0: Better performance, password hashing (Argon2i), secure memory management (memzero), and better security.)
phpmailer/phpmailer suggests installing hayageek/oauth2-yahoo (Needed for Yahoo XOAUTH2 authentication)
phpmailer/phpmailer suggests installing league/oauth2-google (Needed for Google XOAUTH2 authentication)
phpmailer/phpmailer suggests installing stevenmaguire/oauth2-microsoft (Needed for Microsoft XOAUTH2 authentication)
symfony/web-link suggests installing symfony/http-kernel
sebastian/global-state suggests installing ext-uopz (*)
phpunit/phpunit-mock-objects suggests installing ext-soap (*)
phpunit/php-code-coverage suggests installing ext-xdebug (^2.5.5)
phpunit/phpunit suggests installing ext-xdebug (*)
phpunit/phpunit suggests installing phpunit/php-invoker (^1.1)
symfony/event-dispatcher suggests installing symfony/dependency-injection
symfony/event-dispatcher suggests installing symfony/http-kernel
facebook/webdriver suggests installing ext-SimpleXML (For Firefox profile creation)
friendsofphp/php-cs-fixer suggests installing php-cs-fixer/phpunit-constraint-isidenticalstring (For IsIdenticalString constraint.)
friendsofphp/php-cs-fixer suggests installing php-cs-fixer/phpunit-constraint-xmlmatchesxsd (For XmlMatchesXsd constraint.)
consolidation/robo suggests installing henrikbjorn/lurker (For monitoring filesystem changes in taskWatch)
consolidation/robo suggests installing natxet/CssMin (For minifying CSS files in taskMinify)
consolidation/robo suggests installing patchwork/jsqueeze (For minifying JS files in taskMinify)
consolidation/robo suggests installing pear/archive_tar (Allows tar archives to be created and extracted in taskPack and taskExtract, respectively.)
codeception/codeception suggests installing aws/aws-sdk-php (For using AWS Auth in REST module and Queue module)
codeception/codeception suggests installing codeception/phpbuiltinserver (Start and stop PHP built-in web server for your tests)
codeception/codeception suggests installing codeception/specify (BDD-style code blocks)
codeception/codeception suggests installing codeception/verify (BDD-style assertions)
codeception/codeception suggests installing flow/jsonpath (For using JSONPath in REST module)
codeception/codeception suggests installing league/factory-muffin (For DataFactory module)
codeception/codeception suggests installing league/factory-muffin-faker (For Faker support in DataFactory module)
codeception/codeception suggests installing phpseclib/phpseclib (for SFTP option in FTP Module)
codeception/codeception suggests installing stecman/symfony-console-completion (For BASH autocompletion)
codeception/codeception suggests installing symfony/phpunit-bridge (For phpunit-bridge support)
Generating optimized autoload files
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ 
```


```
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ npm install

> node-sass@4.9.3 install /var/www/html/joomla-cms/node_modules/node-sass
> node scripts/install.js

Downloading binary from https://github.com/sass/node-sass/releases/download/v4.9.3/linux-x64-64_binding.node
Download complete  ] - :
Binary saved to /var/www/html/joomla-cms/node_modules/node-sass/vendor/linux-x64-64/binding.node
Caching binary to /home/astrid/.npm/node-sass/4.9.3/linux-x64-64_binding.node

> node-sass@4.9.3 postinstall /var/www/html/joomla-cms/node_modules/node-sass
> node scripts/build.js

Binary found at /var/www/html/joomla-cms/node_modules/node-sass/vendor/linux-x64-64/binding.node
Testing binary
Binary is fine

> joomla@4.0.0 install /var/www/html/joomla-cms
> node build.js --copy-assets && node build.js --build-check

/media/vendor has been removed.
Recreating the media folder...
awesomplete was updated.
bootstrap was updated.
cropperjs was updated.
diff was updated.
dragula was updated.
focus-visible was updated.
font-awesome was updated.
jquery was updated.
jquery-migrate was updated.
joomla-ui-custom-elements was updated.
mediaelement was updated.
punycode was updated.
@claviska/jquery-minicolors was updated.
codemirror was updated.
tinymce was updated.
@webcomponents/webcomponentsjs was updated.
css-vars-ponyfill was updated.
chosen-js was updated.
Minifying legacy stylesheets/scripts...
Processing: /var/www/html/joomla-cms/media/com_associations/css/sidebyside.css
Processing: /var/www/html/joomla-cms/media/com_associations/js/admin-associations-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_associations/js/admin-associations-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_associations/js/associations-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_associations/js/sidebyside.js
Processing: /var/www/html/joomla-cms/media/com_banners/js/admin-banner-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_cache/js/admin-cache-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_config/js/admin-application-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_config/js/config-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_config/js/modules-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_config/js/templates-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_contact/js/admin-contacts-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_contact/js/categories-default.js
Processing: /var/www/html/joomla-cms/media/com_content/js/admin-article-pagebreak.es6.js
Processing: /var/www/html/joomla-cms/media/com_content/js/admin-article-readmore.es6.js
Processing: /var/www/html/joomla-cms/media/com_content/js/admin-articles-default-batch-footer.es6.js
Processing: /var/www/html/joomla-cms/media/com_content/js/admin-articles-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_content/js/form-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_contenthistory/js/admin-compare-compare.es6.js
Processing: /var/www/html/joomla-cms/media/com_contenthistory/js/admin-history-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_fields/js/admin-field-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_fields/js/admin-fields-default-batch.es6.js
Processing: /var/www/html/joomla-cms/media/com_fields/js/admin-fields-modal.js
Processing: /var/www/html/joomla-cms/media/com_finder/css/dates.css
Processing: /var/www/html/joomla-cms/media/com_finder/css/finder.css
Processing: /var/www/html/joomla-cms/media/com_finder/css/indexer.css
Processing: /var/www/html/joomla-cms/media/com_finder/js/filters.es6.js
Processing: /var/www/html/joomla-cms/media/com_finder/js/finder-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_finder/js/finder.es6.js
Processing: /var/www/html/joomla-cms/media/com_finder/js/index.es6.js
Processing: /var/www/html/joomla-cms/media/com_finder/js/indexer.es6.js
Processing: /var/www/html/joomla-cms/media/com_finder/js/maps.es6.js
Processing: /var/www/html/joomla-cms/media/com_installer/css/installer.css
Processing: /var/www/html/joomla-cms/media/com_installer/js/installer.es6.js
Processing: /var/www/html/joomla-cms/media/com_joomlaupdate/js/admin-update-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_joomlaupdate/js/default.js
Processing: /var/www/html/joomla-cms/media/com_joomlaupdate/js/encryption.js
Processing: /var/www/html/joomla-cms/media/com_joomlaupdate/js/update.js
Processing: /var/www/html/joomla-cms/media/com_languages/css/overrider.css
Processing: /var/www/html/joomla-cms/media/com_languages/js/admin-language-edit-change-flag.es6.js
Processing: /var/www/html/joomla-cms/media/com_languages/js/admin-override-edit-refresh-searchstring.es6.js
Processing: /var/www/html/joomla-cms/media/com_languages/js/overrider.es6.js
Processing: /var/www/html/joomla-cms/media/com_mailto/js/mailto-default.js
Processing: /var/www/html/joomla-cms/media/com_media/js/edit-images.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/css/admin-item-edit_container.css
Processing: /var/www/html/joomla-cms/media/com_menus/css/admin-item-edit_modules.css
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit_container.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit_modules.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-item-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-items-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/admin-menus-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_menus/js/default-batch-body.es6.js
Processing: /var/www/html/joomla-cms/media/com_modules/js/admin-module-edit.es6.js
Processing: /var/www/html/joomla-cms/media/com_modules/js/admin-module-edit_assignment.es6.js
Processing: /var/www/html/joomla-cms/media/com_modules/js/admin-modules-modal.es6.js
Processing: /var/www/html/joomla-cms/media/com_newsfeeds/js/categories-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_tags/js/tag-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_tags/js/tag-list.es6.js
Processing: /var/www/html/joomla-cms/media/com_tags/js/tags-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_templates/css/admin-templates-default.css
Processing: /var/www/html/joomla-cms/media/com_templates/js/admin-template-compare.es6.js
Processing: /var/www/html/joomla-cms/media/com_templates/js/admin-template-toggle-switch.es6.js
Processing: /var/www/html/joomla-cms/media/com_templates/js/admin-templates-default.es6.js
Processing: /var/www/html/joomla-cms/media/com_users/js/admin-users-groups.es6.js
Processing: /var/www/html/joomla-cms/media/com_users/js/admin-users-mail.es6.js
Processing: /var/www/html/joomla-cms/media/com_users/js/admin-users-user.es6.js
Processing: /var/www/html/joomla-cms/media/com_users/js/two-factor-switcher.es6.js
Processing: /var/www/html/joomla-cms/media/com_wrapper/js/iframe-height.es6.js
Processing: /var/www/html/joomla-cms/media/editors/codemirror/css/codemirror.css
Processing: /var/www/html/joomla-cms/media/editors/tinymce/css/tinymce-builder.css
Processing: /var/www/html/joomla-cms/media/editors/tinymce/js/plugins/dragdrop/plugin.es6.js
Processing: /var/www/html/joomla-cms/media/editors/tinymce/js/tinymce-builder.js
Processing: /var/www/html/joomla-cms/media/editors/tinymce/js/tinymce.es6.js
Processing: /var/www/html/joomla-cms/media/layouts/js/joomla/html/batch/batch-language.es6.js
Processing: /var/www/html/joomla-cms/media/legacy/css/sortablelist.css
Processing: /var/www/html/joomla-cms/media/legacy/js/ajax-chosen.js
Processing: /var/www/html/joomla-cms/media/legacy/js/bootstrap-init.js
Processing: /var/www/html/joomla-cms/media/legacy/js/frontediting.js
Processing: /var/www/html/joomla-cms/media/legacy/js/helpsite.js
Processing: /var/www/html/joomla-cms/media/legacy/js/highlighter.js
Processing: /var/www/html/joomla-cms/media/legacy/js/html5.js
Processing: /var/www/html/joomla-cms/media/legacy/js/html5fallback.js
Processing: /var/www/html/joomla-cms/media/legacy/js/joomla-chosen.js
Processing: /var/www/html/joomla-cms/media/legacy/js/jquery-noconflict.js
Processing: /var/www/html/joomla-cms/media/legacy/js/sortablelist.js
Processing: /var/www/html/joomla-cms/media/legacy/js/tabs-state.js
Processing: /var/www/html/joomla-cms/media/legacy/js/toolbar.js
Processing: /var/www/html/joomla-cms/media/legacy/js/treeselectmenu.js
Processing: /var/www/html/joomla-cms/media/mod_languages/css/template.css
Processing: /var/www/html/joomla-cms/media/mod_login/js/admin-login.es6.js
Processing: /var/www/html/joomla-cms/media/mod_menu/js/admin-menu.js
Processing: /var/www/html/joomla-cms/media/mod_multilangstatus/js/admin-multilangstatus.es6.js
Processing: /var/www/html/joomla-cms/media/mod_sampledata/js/sampledata-process.es6.js
Processing: /var/www/html/joomla-cms/media/plg_captcha_recaptcha/js/recaptcha.es6.js
Processing: /var/www/html/joomla-cms/media/plg_installer_webinstaller/js/client.es6.js
Processing: /var/www/html/joomla-cms/media/plg_media-action_crop/js/crop.es6.js
Processing: /var/www/html/joomla-cms/media/plg_media-action_resize/js/resize.es6.js
Processing: /var/www/html/joomla-cms/media/plg_media-action_rotate/js/rotate.es6.js
Processing: /var/www/html/joomla-cms/media/plg_quickicon_extensionupdate/js/extensionupdatecheck.es6.js
Processing: /var/www/html/joomla-cms/media/plg_quickicon_joomlaupdate/js/jupdatecheck.es6.js
Processing: /var/www/html/joomla-cms/media/plg_quickicon_overridecheck/js/overridecheck.es6.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/css/debug.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/js/debug.es6.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/info/widget.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/info/widget.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageErrors/widget.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageErrors/widget.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageFiles/widget.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageFiles/widget.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageStrings/widget.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/languageStrings/widget.js
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/sqlqueries/widget.css
Processing: /var/www/html/joomla-cms/media/plg_system_debug/widgets/sqlqueries/widget.js
Processing: /var/www/html/joomla-cms/media/plg_system_highlight/highlight.css
Processing: /var/www/html/joomla-cms/media/plg_system_stats/js/stats-message.es6.js
Processing: /var/www/html/joomla-cms/media/plg_system_stats/js/stats.js
Processing: /var/www/html/joomla-cms/media/system/css/adminlist.css
Processing: /var/www/html/joomla-cms/media/system/css/calendar-jos.css
Processing: /var/www/html/joomla-cms/media/system/css/debug.css
Processing: /var/www/html/joomla-cms/media/system/css/fields/calendar-rtl.css
Processing: /var/www/html/joomla-cms/media/system/css/fields/calendar.css
Processing: /var/www/html/joomla-cms/media/system/css/frontediting.css
Processing: /var/www/html/joomla-cms/media/system/css/mootree.css
Processing: /var/www/html/joomla-cms/media/system/css/mootree_rtl.css
Processing: /var/www/html/joomla-cms/media/system/css/searchtools.css
Processing: /var/www/html/joomla-cms/media/system/css/sortablelist.css
Processing: /var/www/html/joomla-cms/media/system/css/system.css
Processing: /var/www/html/joomla-cms/media/system/js/core.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/draggable.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/af.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ar.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/bg.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/bn.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/bs.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ca.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/cs.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/cy.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/da.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/date/gregorian/date-helper.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/date/jalali/date-helper.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/de.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/el.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/en.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/es.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/eu.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/fa-ir.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/fi.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/fr.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ga.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/hr.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/hu.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/it.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ja.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ka.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ko.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/mk.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/nb.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/nl.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/pl.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/prs-af.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/pt.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ru.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sk.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sl.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sr-rs.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sr-yu.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sv.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/sw.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/ta.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/th.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/uk.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/zh-CN.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar-locales/zh-TW.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/calendar.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/color-field-adv-init.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/modal-fields.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/passwordstrength.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/passwordview.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/select-colour.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/tag.js
Processing: /var/www/html/joomla-cms/media/system/js/fields/validate.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/keepalive.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/multiselect.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/searchtools.es6.js
Processing: /var/www/html/joomla-cms/media/system/js/showon.es6.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/comment/comment.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/comment/continuecomment.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/dialog/dialog.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/display/autorefresh.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/display/fullscreen.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/display/panel.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/display/placeholder.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/display/rulers.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/closebrackets.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/closetag.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/continuelist.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/matchbrackets.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/matchtags.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/edit/trailingspace.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/brace-fold.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/comment-fold.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/foldcode.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/foldgutter.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/indent-fold.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/markdown-fold.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/fold/xml-fold.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/anyword-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/css-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/html-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/javascript-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/show-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/sql-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/hint/xml-hint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/coffeescript-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/css-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/html-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/javascript-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/json-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/lint/yaml-lint.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/merge/merge.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/mode/loadmode.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/mode/multiplex.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/mode/multiplex_test.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/mode/overlay.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/mode/simple.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/runmode/colorize.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/runmode/runmode-standalone.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/runmode/runmode.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/runmode/runmode.node.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/scroll/annotatescrollbar.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/scroll/scrollpastend.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/scroll/simplescrollbars.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/search/jump-to-line.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/search/match-highlighter.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/search/matchesonscrollbar.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/search/search.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/search/searchcursor.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/selection/active-line.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/selection/mark-selection.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/selection/selection-pointer.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/tern/tern.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/tern/worker.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/addon/wrap/hardwrap.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/keymap/emacs.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/keymap/sublime.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/keymap/vim.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/lib/addons.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/lib/codemirror.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/apl/apl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/asciiarmor/asciiarmor.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/asn.1/asn.1.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/asterisk/asterisk.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/brainfuck/brainfuck.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/clike/clike.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/clojure/clojure.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/cmake/cmake.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/cobol/cobol.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/coffeescript/coffeescript.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/commonlisp/commonlisp.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/crystal/crystal.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/css/css.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/cypher/cypher.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/d/d.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/dart/dart.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/diff/diff.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/django/django.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/dockerfile/dockerfile.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/dtd/dtd.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/dylan/dylan.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ebnf/ebnf.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ecl/ecl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/eiffel/eiffel.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/elm/elm.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/erlang/erlang.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/factor/factor.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/fcl/fcl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/forth/forth.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/fortran/fortran.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/gas/gas.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/gfm/gfm.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/gherkin/gherkin.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/go/go.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/groovy/groovy.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/haml/haml.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/handlebars/handlebars.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/haskell/haskell.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/haskell-literate/haskell-literate.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/haxe/haxe.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/htmlembedded/htmlembedded.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/htmlmixed/htmlmixed.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/http/http.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/idl/idl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/javascript/javascript.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/jinja2/jinja2.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/jsx/jsx.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/julia/julia.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/livescript/livescript.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/lua/lua.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/markdown/markdown.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mathematica/mathematica.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mbox/mbox.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/meta.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mirc/mirc.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mllike/mllike.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/modelica/modelica.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mscgen/mscgen.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/mumps/mumps.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/nginx/nginx.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/nsis/nsis.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ntriples/ntriples.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/octave/octave.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/oz/oz.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/pascal/pascal.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/pegjs/pegjs.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/perl/perl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/php/php.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/pig/pig.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/powershell/powershell.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/properties/properties.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/protobuf/protobuf.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/pug/pug.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/puppet/puppet.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/python/python.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/q/q.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/r/r.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/rpm/rpm.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/rst/rst.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ruby/ruby.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/rust/rust.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/sas/sas.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/sass/sass.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/scheme/scheme.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/shell/shell.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/sieve/sieve.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/slim/slim.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/smalltalk/smalltalk.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/smarty/smarty.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/solr/solr.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/soy/soy.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/sparql/sparql.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/spreadsheet/spreadsheet.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/sql/sql.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/stex/stex.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/stylus/stylus.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/swift/swift.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/tcl/tcl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/textile/textile.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/tiddlywiki/tiddlywiki.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/tiki/tiki.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/toml/toml.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/tornado/tornado.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/troff/troff.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ttcn/ttcn.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/ttcn-cfg/ttcn-cfg.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/turtle/turtle.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/twig/twig.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/vb/vb.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/vbscript/vbscript.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/velocity/velocity.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/verilog/verilog.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/vhdl/vhdl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/vue/vue.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/webidl/webidl.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/xml/xml.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/xquery/xquery.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/yacas/yacas.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/yaml/yaml.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/yaml-frontmatter/yaml-frontmatter.js
Processing: /var/www/html/joomla-cms/media/vendor/codemirror/mode/z80/z80.js
Processing: /var/www/html/joomla-cms/media/vendor/jquery-ui/js/jquery.ui.core.js
Processing: /var/www/html/joomla-cms/media/vendor/jquery-ui/js/jquery.ui.sortable.js
Processing: /var/www/html/joomla-cms/media/vendor/punycode/js/punycode.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/af.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ar.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/be.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/bg.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/bs.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ca.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/cs.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/cy.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/da.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/de.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/el.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/es.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/et.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/eu.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/fa.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/fi.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/fo.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/fr.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ga.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/gl.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/he.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/hr.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/hu.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/id.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/it.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ja.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ka.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/km.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ko.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/lb.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/lt.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/lv.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/mk.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ms.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/nb.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/nl.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/pl.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/pt-BR.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/pt-PT.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ro.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ru.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/si-LK.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sk.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sl.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sr.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sv.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sw.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/sy.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ta.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/th.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/tr.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/ug.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/uk.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/vi.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/zh-CN.js
Processing: /var/www/html/joomla-cms/media/vendor/tinymce/langs/zh-TW.js
Processing: /var/www/html/joomla-cms/media/vendor/webcomponentsjs/js/webcomponents-ce.js
Processing: /var/www/html/joomla-cms/media/vendor/webcomponentsjs/js/webcomponents-sd-ce-pf.js
Processing: /var/www/html/joomla-cms/media/vendor/webcomponentsjs/js/webcomponents-sd-ce.js
Processing: /var/www/html/joomla-cms/media/vendor/webcomponentsjs/js/webcomponents-sd.js
The /templates/system/incompatible.html page was created successfully!
The /templates/system/build_incomplete.html page was created successfully!

> joomla@4.0.0 postinstall /var/www/html/joomla-cms
> node build.js --compile-js && node build.js --compile-css && node build.js --compile-ce &&cd administrator/components/com_media && npm install && npm run build

Compiling: /var/www/html/joomla-cms/media/com_associations/js/admin-associations-modal.js
Compiling: /var/www/html/joomla-cms/media/com_associations/js/associations-edit.js
Compiling: /var/www/html/joomla-cms/media/com_associations/js/admin-associations-default.js
Compiling: /var/www/html/joomla-cms/media/com_banners/js/admin-banner-edit.js
Compiling: /var/www/html/joomla-cms/media/com_cache/js/admin-cache-default.js
Compiling: /var/www/html/joomla-cms/media/com_config/js/admin-application-default.js
Compiling: /var/www/html/joomla-cms/media/com_config/js/config-default.js
Compiling: /var/www/html/joomla-cms/media/com_config/js/modules-default.js
Compiling: /var/www/html/joomla-cms/media/com_contact/js/admin-contacts-modal.js
Compiling: /var/www/html/joomla-cms/media/com_config/js/templates-default.js
Compiling: /var/www/html/joomla-cms/media/com_content/js/admin-article-pagebreak.js
Compiling: /var/www/html/joomla-cms/media/com_content/js/admin-article-readmore.js
Compiling: /var/www/html/joomla-cms/media/com_content/js/admin-articles-default-batch-footer.js
Compiling: /var/www/html/joomla-cms/media/com_content/js/admin-articles-modal.js
Compiling: /var/www/html/joomla-cms/media/com_content/js/form-edit.js
Compiling: /var/www/html/joomla-cms/media/com_contenthistory/js/admin-compare-compare.js
Compiling: /var/www/html/joomla-cms/media/com_fields/js/admin-field-edit.js
Compiling: /var/www/html/joomla-cms/media/com_fields/js/admin-fields-default-batch.js
Compiling: /var/www/html/joomla-cms/media/com_contenthistory/js/admin-history-modal.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/filters.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/finder-edit.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/finder.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/index.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/indexer.js
Compiling: /var/www/html/joomla-cms/media/com_finder/js/maps.js
Compiling: /var/www/html/joomla-cms/media/com_installer/js/installer.js
Compiling: /var/www/html/joomla-cms/media/com_joomlaupdate/js/admin-update-default.js
Compiling: /var/www/html/joomla-cms/media/com_languages/js/admin-language-edit-change-flag.js
Compiling: /var/www/html/joomla-cms/media/com_languages/js/overrider.js
Compiling: /var/www/html/joomla-cms/media/com_languages/js/admin-override-edit-refresh-searchstring.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit_container.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-item-edit_modules.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-item-modal.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-items-modal.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/admin-menus-default.js
Compiling: /var/www/html/joomla-cms/media/com_menus/js/default-batch-body.js
Compiling: /var/www/html/joomla-cms/media/com_modules/js/admin-module-edit_assignment.js
Compiling: /var/www/html/joomla-cms/media/com_modules/js/admin-module-edit.js
Compiling: /var/www/html/joomla-cms/media/com_modules/js/admin-modules-modal.js
Compiling: /var/www/html/joomla-cms/media/com_newsfeeds/js/categories-default.js
Compiling: /var/www/html/joomla-cms/media/com_tags/js/tag-default.js
Compiling: /var/www/html/joomla-cms/media/com_tags/js/tag-list.js
Compiling: /var/www/html/joomla-cms/media/com_tags/js/tags-default.js
Compiling: /var/www/html/joomla-cms/media/com_templates/js/admin-template-toggle-switch.js
Compiling: /var/www/html/joomla-cms/media/com_users/js/admin-users-groups.js
Compiling: /var/www/html/joomla-cms/media/com_templates/js/admin-template-compare.js
Compiling: /var/www/html/joomla-cms/media/com_users/js/admin-users-mail.js
Compiling: /var/www/html/joomla-cms/media/com_users/js/admin-users-user.js
Compiling: /var/www/html/joomla-cms/media/com_users/js/two-factor-switcher.js
Compiling: /var/www/html/joomla-cms/media/com_wrapper/js/iframe-height.js
Compiling: /var/www/html/joomla-cms/media/mod_multilangstatus/js/admin-multilangstatus.js
Compiling: /var/www/html/joomla-cms/media/mod_sampledata/js/sampledata-process.js
Compiling: /var/www/html/joomla-cms/media/mod_login/js/admin-login.js
Compiling: /var/www/html/joomla-cms/media/plg_captcha_recaptcha/js/recaptcha.js
Compiling: /var/www/html/joomla-cms/media/plg_media-action_crop/js/crop.js
Compiling: /var/www/html/joomla-cms/media/plg_media-action_resize/js/resize.js
Compiling: /var/www/html/joomla-cms/media/plg_media-action_rotate/js/rotate.js
Compiling: /var/www/html/joomla-cms/media/plg_quickicon_extensionupdate/js/extensionupdatecheck.js
Compiling: /var/www/html/joomla-cms/media/plg_quickicon_joomlaupdate/js/jupdatecheck.js
Compiling: /var/www/html/joomla-cms/media/plg_quickicon_overridecheck/js/overridecheck.js
Compiling: /var/www/html/joomla-cms/media/plg_system_debug/js/debug.js
Compiling: /var/www/html/joomla-cms/media/plg_system_stats/js/stats-message.js
Compiling: /var/www/html/joomla-cms/media/system/js/multiselect.js
Compiling: /var/www/html/joomla-cms/media/system/js/keepalive.js
Compiling: /var/www/html/joomla-cms/media/system/js/fields/select-colour.js
Compiling: /var/www/html/joomla-cms/media/editors/tinymce/js/tinymce.js
Compiling: /var/www/html/joomla-cms/media/editors/tinymce/js/plugins/dragdrop/plugin.js
Compiling: /var/www/html/joomla-cms/media/layouts/js/joomla/html/batch/batch-language.js
Compiling: /var/www/html/joomla-cms/media/com_media/js/edit-images.js
Compiling: /var/www/html/joomla-cms/media/com_templates/js/admin-templates-default.js
Compiling: /var/www/html/joomla-cms/media/plg_installer_webinstaller/js/client.js
Compiling: /var/www/html/joomla-cms/media/system/js/searchtools.js
Compiling: /var/www/html/joomla-cms/media/system/js/showon.js
Compiling: /var/www/html/joomla-cms/media/system/js/fields/validate.js
Compiling: /var/www/html/joomla-cms/media/system/js/core.js
Prefixing for: last 1 version,not ie < 11
File: offline.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: font-awesome.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template-rtl.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: client.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: bootstrap.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template-rtl.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template-rtl.css was updated. 
Prefixing for: last 1 version,not ie < 11
File: template.css was updated. 
Prefixing for: last 1 version,not ie < 11
Prefixing for: last 1 version,not ie < 11
Prefixing for: last 1 version,not ie < 11

> node-sass@4.9.3 install /var/www/html/joomla-cms/administrator/components/com_media/node_modules/node-sass
> node scripts/install.js

Cached binary found at /home/astrid/.npm/node-sass/4.9.3/linux-x64-64_binding.node

> uglifyjs-webpack-plugin@0.4.6 postinstall /var/www/html/joomla-cms/administrator/components/com_media/node_modules/uglifyjs-webpack-plugin
> node lib/post_install.js


> node-sass@4.9.3 postinstall /var/www/html/joomla-cms/administrator/components/com_media/node_modules/node-sass
> node scripts/build.js

Binary found at /var/www/html/joomla-cms/administrator/components/com_media/node_modules/node-sass/vendor/linux-x64-64/binding.node
Testing binary
Binary is fine
npm WARN com_media@4.0.0 No repository field.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 768 packages from 564 contributors and audited 8538 packages in 17.132s
found 0 vulnerabilities


> com_media@4.0.0 build /var/www/html/joomla-cms/administrator/components/com_media
> cross-env NODE_ENV=production webpack --progress --hide-modules

 10% building modules 0/1 modules 1 active ... ./resources/styles/mediamanager.s 10% building modules 1/2 modules 1 active ...dia/resources/scripts/mediamanager 10% building modules 1/3 modules 2 active ...ia/resources/styles/mediamanager.s 10% building modules 2/3 modules 1 active ...ia/resources/styles/mediamanager.s 10% building modules 2/4 modules 2 active ..._media/resources/scripts/app/Event 10% building modules 2/5 modules 3 active ...ipts/components/browser/items/item 10% building modules 2/6 modules 4 active ...esources/scripts/plugins/translate 10% building modules 2/7 modules 5 active ...edia/resources/scripts/store/store 10% building modules 2/8 modules 6 active ...edia/node_modules/vue/dist/vue.esm 10% building modules 3/8 modules 5 active ...edia/node_modules/vue/dist/vue.esm 10% building modules 4/8 modules 4 active ...edia/node_modules/vue/dist/vue.esm 10% building modules 5/8 modules 3 active ...edia/node_modules/vue/dist/vue.esm 10% building modules 6/8 modules 2 active ...edia/node_modules/vue/dist/vue.esm 10% building modules 6/9 modules 3 active ...urces/scripts/store/mutation-types 10% building modules 6/10 modules 4 active ...edia/resources/scripts/store/stat 10% building modules 6/11 modules 5 active ...ia/resources/scripts/store/getter 10% building modules 6/12 modules 6 active ...ia/resources/scripts/store/action 10% building modules 6/13 modules 7 active .../resources/scripts/store/mutation 10% building modules 6/14 modules 8 active ...ipts/store/plugins/persisted-stat 10% building modules 6/15 modules 9 active .../resources/scripts/components/app 10% building modules 6/16 modules 10 active ...rces/scripts/components/tree/dis 10% building modules 6/17 modules 11 active ...ces/scripts/components/tree/driv 10% building modules 6/18 modules 12 active ...rces/scripts/components/tree/tre 10% building modules 6/19 modules 13 active ...rces/scripts/components/tree/ite 10% building modules 6/20 modules 14 active ...cripts/components/toolbar/toolba 10% building modules 6/21 modules 15 active .../components/breadcrumb/breadcrum 10% building modules 6/22 modules 16 active ...cripts/components/browser/browse 10% building modules 6/23 modules 17 active ...s/scripts/components/modals/moda 10% building modules 6/24 modules 18 active ...onents/modals/create-folder-moda 10% building modules 6/25 modules 19 active ...s/components/modals/preview-moda 10% building modules 6/26 modules 20 active ...ts/components/modals/rename-moda 10% building modules 6/27 modules 21 active ...pts/components/modals/share-moda 10% building modules 6/28 modules 22 active ...nents/modals/confirm-delete-moda 10% building modules 6/29 modules 23 active ...cripts/components/infobar/infoba 10% building modules 6/30 modules 24 active .../scripts/components/upload/uploa 10% building modules 6/31 modules 25 active ...omponents/browser/items/director 10% building modules 6/32 modules 26 active ...pts/components/browser/items/fil 10% building modules 6/33 modules 27 active ...ts/components/browser/items/imag 10% building modules 6/34 modules 28 active ...ts/components/browser/items/vide 10% building modules 6/35 modules 29 active ...ipts/components/browser/items/ro 10% building modules 7/35 modules 28 active ...ipts/components/browser/items/ro 10% building modules 8/35 modules 27 active ...ipts/components/browser/items/ro 11% building modules 9/35 modules 26 active ...ipts/components/browser/items/ro 11% building modules 10/35 modules 25 active ...ipts/components/browser/items/r 11% building modules 10/36 modules 26 active ...bel-runtime/helpers/classCallCh 11% building modules 10/37 modules 27 active .../babel-runtime/helpers/createCl 11% building modules 11/37 modules 26 active .../babel-runtime/helpers/createCl 11% building modules 12/37 modules 25 active .../babel-runtime/helpers/createCl 11% building modules 13/37 modules 24 active .../babel-runtime/helpers/createCl 11% building modules 14/37 modules 23 active .../babel-runtime/helpers/createCl 11% building modules 15/37 modules 22 active .../babel-runtime/helpers/createCl 11% building modules 16/37 modules 21 active .../babel-runtime/helpers/createCl 12% building modules 17/37 modules 20 active .../babel-runtime/helpers/createCl 12% building modules 18/37 modules 19 active .../babel-runtime/helpers/createCl 12% building modules 19/37 modules 18 active .../babel-runtime/helpers/createCl 12% building modules 20/37 modules 17 active .../babel-runtime/helpers/createCl 12% building modules 21/37 modules 16 active .../babel-runtime/helpers/createCl 12% building modules 22/37 modules 15 active .../babel-runtime/helpers/createCl 12% building modules 23/37 modules 14 active .../babel-runtime/helpers/createCl 12% building modules 24/37 modules 13 active .../babel-runtime/helpers/createCl 13% building modules 25/37 modules 12 active .../babel-runtime/helpers/createCl 13% building modules 26/37 modules 11 active .../babel-runtime/helpers/createCl 13% building modules 27/37 modules 10 active .../babel-runtime/helpers/createCl 13% building modules 28/37 modules 9 active .../babel-runtime/helpers/createCla 13% building modules 29/37 modules 8 active .../babel-runtime/helpers/createCla 13% building modules 30/37 modules 7 active .../babel-runtime/helpers/createCla 13% building modules 31/37 modules 6 active .../babel-runtime/helpers/createCla 13% building modules 32/37 modules 5 active .../babel-runtime/helpers/createCla 13% building modules 33/37 modules 4 active .../babel-runtime/helpers/createCla 14% building modules 34/37 modules 3 active .../babel-runtime/helpers/createCla 14% building modules 35/37 modules 2 active ...edia/node_modules/vue/dist/vue.e 14% building modules 35/38 modules 3 active ...-runtime/helpers/toConsumableArr 14% building modules 35/39 modules 4 active ...om_media/resources/scripts/app/A 14% building modules 35/40 modules 5 active ...esources/scripts/app/Notificatio 14% building modules 35/41 modules 6 active ...ia/node_modules/vuex/dist/vuex.e 14% building modules 35/42 modules 7 active ...dstate/dist/vuex-persistedstate. 14% building modules 35/43 modules 8 active ...bel-runtime/helpers/defineProper 14% building modules 35/44 modules 9 active ...bel-runtime/core-js/json/stringi 14% building modules 35/45 modules 10 active ...abel-runtime/core-js/object/ass 14% building modules 35/46 modules 11 active ...ue-loader/lib/component-normali 14% building modules 35/47 modules 12 active .../resources/scripts/components/a 14% building modules 35/48 modules 13 active ...rces/scripts/components/tree/di 14% building modules 35/49 modules 14 active ...ces/scripts/components/tree/dri 14% building modules 35/50 modules 15 active ...rces/scripts/components/tree/tr 14% building modules 35/51 modules 16 active ...rces/scripts/components/tree/it 14% building modules 35/52 modules 17 active ...cripts/components/toolbar/toolb 14% building modules 35/53 modules 18 active .../components/breadcrumb/breadcru 14% building modules 35/54 modules 19 active ...cripts/components/browser/brows 14% building modules 35/55 modules 20 active ...s/scripts/components/modals/mod 14% building modules 35/56 modules 21 active ...onents/modals/create-folder-mod 14% building modules 35/57 modules 22 active ...s/components/modals/preview-mod 14% building modules 35/58 modules 23 active ...ts/components/modals/rename-mod 14% building modules 35/59 modules 24 active ...pts/components/modals/share-mod 14% building modules 35/60 modules 25 active ...nents/modals/confirm-delete-mod 14% building modules 35/61 modules 26 active ...cripts/components/infobar/infob 14% building modules 35/62 modules 27 active .../scripts/components/upload/uplo 14% building modules 35/63 modules 28 active ...omponents/browser/items/directo 14% building modules 35/64 modules 29 active ...pts/components/browser/items/fi 14% building modules 35/65 modules 30 active ...ts/components/browser/items/ima 14% building modules 35/66 modules 31 active ...ts/components/browser/items/vid 14% building modules 35/67 modules 32 active ...ipts/components/browser/items/r 14% building modules 36/67 modules 31 active ...ipts/components/browser/items/r 14% building modules 37/67 modules 30 active ...ipts/components/browser/items/r 14% building modules 38/67 modules 29 active ...ipts/components/browser/items/r 14% building modules 39/67 modules 28 active ...ipts/components/browser/items/r 14% building modules 40/67 modules 27 active ...ipts/components/browser/items/r 14% building modules 41/67 modules 26 active ...ipts/components/browser/items/r 15% building modules 42/67 modules 25 active ...ipts/components/browser/items/r 15% building modules 43/67 modules 24 active ...ipts/components/browser/items/r 15% building modules 44/67 modules 23 active ...ipts/components/browser/items/r 15% building modules 45/67 modules 22 active ...ipts/components/browser/items/r 15% building modules 46/67 modules 21 active ...ipts/components/browser/items/r 15% building modules 47/67 modules 20 active ...ipts/components/browser/items/r 15% building modules 48/67 modules 19 active ...ipts/components/browser/items/r 15% building modules 49/67 modules 18 active ...ipts/components/browser/items/r 16% building modules 50/67 modules 17 active ...ipts/components/browser/items/r 16% building modules 51/67 modules 16 active ...ipts/components/browser/items/r 16% building modules 52/67 modules 15 active ...ipts/components/browser/items/r 16% building modules 53/67 modules 14 active ...ipts/components/browser/items/r 16% building modules 54/67 modules 13 active ...ipts/components/browser/items/r 16% building modules 55/67 modules 12 active ...ipts/components/browser/items/r 16% building modules 56/67 modules 11 active ...ue-loader/lib/component-normali 16% building modules 56/68 modules 12 active .../resources/scripts/components/a 16% building modules 56/69 modules 13 active ...rces/scripts/components/tree/di 16% building modules 56/70 modules 14 active ...ces/scripts/components/tree/dri 16% building modules 56/71 modules 15 active ...rces/scripts/components/tree/tr 16% building modules 56/72 modules 16 active ...rces/scripts/components/tree/it 16% building modules 56/73 modules 17 active ...cripts/components/toolbar/toolb 16% building modules 56/74 modules 18 active .../components/breadcrumb/breadcru 16% building modules 56/75 modules 19 active ...cripts/components/browser/brows 16% building modules 56/76 modules 20 active ...s/scripts/components/modals/mod 16% building modules 56/77 modules 21 active ...onents/modals/create-folder-mod 16% building modules 56/78 modules 22 active ...s/components/modals/preview-mod 16% building modules 56/79 modules 23 active ...ts/components/modals/rename-mod 16% building modules 56/80 modules 24 active ...pts/components/modals/share-mod 16% building modules 56/81 modules 25 active ...nents/modals/confirm-delete-mod 16% building modules 56/82 modules 26 active ...cripts/components/infobar/infob 16% building modules 56/83 modules 27 active .../scripts/components/upload/uplo 16% building modules 56/84 modules 28 active ...omponents/browser/items/directo 16% building modules 56/85 modules 29 active ...pts/components/browser/items/fi 16% building modules 56/86 modules 30 active ...ts/components/browser/items/ima 16% building modules 56/87 modules 31 active ...ts/components/browser/items/vid 16% building modules 56/88 modules 32 active ...ipts/components/browser/items/r 16% building modules 57/88 modules 31 active ...ipts/components/browser/items/r 16% building modules 58/88 modules 30 active ...ipts/components/browser/items/r 17% building modules 59/88 modules 29 active ...ipts/components/browser/items/r 17% building modules 60/88 modules 28 active ...ipts/components/browser/items/r 17% building modules 61/88 modules 27 active ...ipts/components/browser/items/r 17% building modules 62/88 modules 26 active ...ipts/components/browser/items/r 17% building modules 63/88 modules 25 active ...ipts/components/browser/items/r 17% building modules 64/88 modules 24 active ...ipts/components/browser/items/r 17% building modules 65/88 modules 23 active ...ipts/components/browser/items/r 17% building modules 66/88 modules 22 active ...ipts/components/browser/items/r 18% building modules 67/88 modules 21 active ...ipts/components/browser/items/r 18% building modules 68/88 modules 20 active ...ipts/components/browser/items/r 18% building modules 69/88 modules 19 active ...ipts/components/browser/items/r 18% building modules 70/88 modules 18 active ...ipts/components/browser/items/r 18% building modules 71/88 modules 17 active ...ipts/components/browser/items/r 18% building modules 72/88 modules 16 active ...ipts/components/browser/items/r 18% building modules 73/88 modules 15 active ...ipts/components/browser/items/r 18% building modules 74/88 modules 14 active ...ipts/components/browser/items/r 19% building modules 75/88 modules 13 active ...ipts/components/browser/items/r 19% building modules 76/88 modules 12 active ...ipts/components/browser/items/r 19% building modules 77/88 modules 11 active ...ue-loader/lib/component-normali 19% building modules 77/89 modules 12 active ...node_modules/path-browserify/in 19% building modules 78/89 modules 11 active ...node_modules/path-browserify/in 19% building modules 79/89 modules 10 active ...node_modules/path-browserify/in 19% building modules 80/89 modules 9 active ...node_modules/path-browserify/ind 19% building modules 80/90 modules 10 active .../node_modules/file-saver/FileSa 19% building modules 81/90 modules 9 active .../node_modules/file-saver/FileSav 19% building modules 81/91 modules 10 active ...ime/core-js/object/define-prope 19% building modules 82/91 modules 9 active ...ime/core-js/object/define-proper 19% building modules 83/91 modules 8 active ...ime/core-js/object/define-proper 20% building modules 84/91 modules 7 active ...ime/core-js/object/define-proper 20% building modules 85/91 modules 6 active ...ime/core-js/object/define-proper 20% building modules 86/91 modules 5 active ...ime/core-js/object/define-proper 20% building modules 87/91 modules 4 active ...ime/core-js/object/define-proper 20% building modules 87/92 modules 5 active ...babel-runtime/core-js/get-iterat 20% building modules 88/92 modules 4 active ...babel-runtime/core-js/get-iterat 20% building modules 89/92 modules 3 active ...babel-runtime/core-js/get-iterat 20% building modules 89/93 modules 4 active ...resources/scripts/mixins/navigab 20% building modules 89/94 modules 5 active ...ules/babel-runtime/core-js/promi 20% building modules 89/95 modules 6 active ...s/babel-runtime/core-js/array/fr 20% building modules 90/95 modules 5 active ...s/babel-runtime/core-js/array/fr 20% building modules 91/95 modules 4 active ...s/babel-runtime/core-js/array/fr 21% building modules 92/95 modules 3 active ...s/babel-runtime/core-js/array/fr 21% building modules 93/95 modules 2 active ...edia/node_modules/vue/dist/vue.e 21% building modules 93/96 modules 3 active ...media/node_modules/process/brows 21% building modules 93/97 modules 4 active ...modules/webpack/buildin/amd-defi 21% building modules 93/98 modules 5 active ...odules/webpack/buildin/amd-optio 21% building modules 93/99 modules 6 active ...es/vue-focus/dist/vue-focus.comm 21% building modules 93/100 modules 7 active .../core-js/library/fn/json/string 21% building modules 93/101 modules 8 active ...s/core-js/library/fn/object/ass 21% building modules 93/102 modules 9 active .../library/fn/object/define-prope 21% building modules 93/103 modules 10 active ...es/core-js/library/fn/get-iter 21% building modules 93/104 modules 11 active ...modules/core-js/library/fn/pro 21% building modules 94/104 modules 10 active ...modules/core-js/library/fn/pro 21% building modules 94/105 modules 11 active ...dia/node_modules/deepmerge/dis 21% building modules 94/106 modules 12 active ...dia/node_modules/shvl/dist/shv 21% building modules 94/107 modules 13 active ...ules/core-js/library/fn/array/ 21% building modules 95/107 modules 12 active ...ules/core-js/library/fn/array/ 21% building modules 96/107 modules 11 active ...ules/core-js/library/fn/array/ 21% building modules 97/107 modules 10 active ...ules/core-js/library/fn/array/ 21% building modules 98/107 modules 9 active ...ules/core-js/library/fn/array/f 21% building modules 99/107 modules 8 active ...ules/core-js/library/fn/array/f 22% building modules 100/107 modules 7 active ...ules/core-js/library/fn/array/ 22% building modules 101/107 modules 6 active ...ules/core-js/library/fn/array/ 22% building modules 102/107 modules 5 active ...ules/core-js/library/fn/array/ 22% building modules 103/107 modules 4 active ...ules/core-js/library/fn/array/ 22% building modules 104/107 modules 3 active ...ules/core-js/library/fn/array/ 22% building modules 105/107 modules 2 active ...ules/core-js/library/fn/array/ 22% building modules 106/107 modules 1 active ...ia/resources/styles/mediamanag 22% building modules 106/108 modules 2 active ...ode_modules/webpack/buildin/gl 22% building modules 106/109 modules 3 active ...ules/core-js/library/modules/_ 22% building modules 106/110 modules 4 active .../library/modules/es6.object.as 22% building modules 106/111 modules 5 active ...modules/es6.object.define-prop 22% building modules 106/112 modules 6 active ...s/library/modules/web.dom.iter 22% building modules 106/113 modules 7 active ...ibrary/modules/es6.string.iter 22% building modules 106/114 modules 8 active .../library/modules/core.get-iter 22% building modules 106/115 modules 9 active ...brary/modules/es6.object.to-st 22% building modules 106/116 modules 10 active ...ore-js/library/modules/es6.pr 22% building modules 106/117 modules 11 active ...ibrary/modules/es7.promise.fi 22% building modules 106/118 modules 12 active ...js/library/modules/es7.promis 22% building modules 106/119 modules 13 active ...-js/library/modules/es6.array 22% building modules 107/119 modules 12 active ...-js/library/modules/es6.array 22% building modules 107/120 modules 13 active ...ode_modules/timers-browserify 22% building modules 108/120 modules 12 active ...ode_modules/timers-browserify 23% building modules 109/120 modules 11 active ...ode_modules/timers-browserify 23% building modules 110/120 modules 10 active ...ode_modules/timers-browserify 23% building modules 111/120 modules 9 active ...ode_modules/timers-browserify/ 23% building modules 112/120 modules 8 active ...ode_modules/timers-browserify/ 23% building modules 113/120 modules 7 active ...ode_modules/timers-browserify/ 23% building modules 114/120 modules 6 active ...ode_modules/timers-browserify/ 23% building modules 115/120 modules 5 active ...ode_modules/timers-browserify/ 23% building modules 116/120 modules 4 active ...ode_modules/timers-browserify/ 24% building modules 117/120 modules 3 active ...ode_modules/timers-browserify/ 24% building modules 118/120 modules 2 active ...ode_modules/timers-browserify/ 24% building modules 119/120 modules 1 active ...ia/resources/styles/mediamanag 24% building modules 119/121 modules 2 active ...es/core-js/library/modules/_ex 24% building modules 119/122 modules 3 active ...-js/library/modules/_object-as 24% building modules 119/123 modules 4 active ...re-js/library/modules/_descrip 24% building modules 119/124 modules 5 active ...core-js/library/modules/_objec 24% building modules 119/125 modules 6 active ...library/modules/es6.array.iter 24% building modules 119/126 modules 7 active ...es/core-js/library/modules/_gl 24% building modules 119/127 modules 8 active ...ules/core-js/library/modules/_ 24% building modules 119/128 modules 9 active ...core-js/library/modules/_itera 24% building modules 119/129 modules 10 active ...dules/core-js/library/modules 24% building modules 119/130 modules 11 active ...core-js/library/modules/_stri 24% building modules 119/131 modules 12 active ...re-js/library/modules/_iter-d 24% building modules 119/132 modules 13 active ...core-js/library/modules/_an-o 24% building modules 119/133 modules 14 active ...y/modules/core.get-iterator-m 24% building modules 119/134 modules 15 active ...brary/modules/_species-constr 24% building modules 119/135 modules 16 active ...s/library/modules/_promise-re 24% building modules 119/136 modules 17 active ...ry/modules/_new-promise-capab 24% building modules 119/137 modules 18 active ...s/core-js/library/modules/_pe 24% building modules 119/138 modules 19 active ...s/core-js/library/modules/_li 24% building modules 119/139 modules 20 active ...dules/core-js/library/modules 24% building modules 119/140 modules 21 active ...s/core-js/library/modules/_cl 24% building modules 119/141 modules 22 active ...core-js/library/modules/_is-o 24% building modules 119/142 modules 23 active ...ore-js/library/modules/_a-fun 24% building modules 119/143 modules 24 active ...re-js/library/modules/_an-ins 24% building modules 119/144 modules 25 active ...es/core-js/library/modules/_f 24% building modules 119/145 modules 26 active ...ules/core-js/library/modules/ 24% building modules 119/146 modules 27 active ...core-js/library/modules/_micr 24% building modules 119/147 modules 28 active ...ore-js/library/modules/_user- 24% building modules 119/148 modules 29 active ...e-js/library/modules/_redefin 24% building modules 119/149 modules 30 active ...library/modules/_set-to-strin 24% building modules 119/150 modules 31 active ...re-js/library/modules/_set-sp 24% building modules 119/151 modules 32 active ...re-js/library/modules/_iter-d 24% building modules 119/152 modules 33 active ...core-js/library/modules/_to-o 24% building modules 119/153 modules 34 active ...core-js/library/modules/_iter 24% building modules 119/154 modules 35 active ...-js/library/modules/_is-array 24% building modules 119/155 modules 36 active ...core-js/library/modules/_to-l 24% building modules 119/156 modules 37 active ...s/library/modules/_create-pro 24% building modules 120/156 modules 36 active ...s/library/modules/_create-pro 24% building modules 121/156 modules 35 active ...s/library/modules/_create-pro 24% building modules 122/156 modules 34 active ...s/library/modules/_create-pro 24% building modules 123/156 modules 33 active ...s/library/modules/_create-pro 24% building modules 124/156 modules 32 active ...s/library/modules/_create-pro 25% building modules 125/156 modules 31 active ...s/library/modules/_create-pro 25% building modules 126/156 modules 30 active ...s/library/modules/_create-pro 25% building modules 127/156 modules 29 active ...s/library/modules/_create-pro 25% building modules 128/156 modules 28 active ...s/library/modules/_create-pro 25% building modules 129/156 modules 27 active ...s/library/modules/_create-pro 25% building modules 130/156 modules 26 active ...s/library/modules/_create-pro 25% building modules 131/156 modules 25 active ...s/library/modules/_create-pro 25% building modules 132/156 modules 24 active ...s/library/modules/_create-pro 25% building modules 133/156 modules 23 active ...s/library/modules/_create-pro 26% building modules 134/156 modules 22 active ...s/library/modules/_create-pro 26% building modules 135/156 modules 21 active ...s/library/modules/_create-pro 26% building modules 136/156 modules 20 active ...s/library/modules/_create-pro 26% building modules 137/156 modules 19 active ...s/library/modules/_create-pro 26% building modules 138/156 modules 18 active ...s/library/modules/_create-pro 26% building modules 139/156 modules 17 active ...s/library/modules/_create-pro 26% building modules 140/156 modules 16 active ...s/library/modules/_create-pro 26% building modules 141/156 modules 15 active ...s/library/modules/_create-pro 27% building modules 142/156 modules 14 active ...s/library/modules/_create-pro 27% building modules 143/156 modules 13 active ...s/library/modules/_create-pro 27% building modules 144/156 modules 12 active ...s/library/modules/_create-pro 27% building modules 145/156 modules 11 active ...s/library/modules/_create-pro 27% building modules 146/156 modules 10 active ...s/library/modules/_create-pro 27% building modules 147/156 modules 9 active ...s/library/modules/_create-prop 27% building modules 148/156 modules 8 active ...s/library/modules/_create-prop 27% building modules 149/156 modules 7 active ...s/library/modules/_create-prop 28% building modules 150/156 modules 6 active ...s/library/modules/_create-prop 28% building modules 151/156 modules 5 active ...s/library/modules/_create-prop 28% building modules 152/156 modules 4 active ...s/library/modules/_create-prop 28% building modules 153/156 modules 3 active ...s/library/modules/_create-prop 28% building modules 154/156 modules 2 active ...s/library/modules/_create-prop 28% building modules 155/156 modules 1 active ...ia/resources/styles/mediamanag 28% building modules 155/157 modules 2 active ...dules/core-js/library/modules/ 28% building modules 155/158 modules 3 active ...re-js/library/modules/_object- 28% building modules 155/159 modules 4 active ...re-js/library/modules/_object- 28% building modules 155/160 modules 5 active ...ore-js/library/modules/_object 28% building modules 155/161 modules 6 active ...s/core-js/library/modules/_iob 28% building modules 155/162 modules 7 active ...les/core-js/library/modules/_f 28% building modules 155/163 modules 8 active ...js/library/modules/_ie8-dom-de 28% building modules 155/164 modules 9 active ...e-js/library/modules/_to-primi 28% building modules 155/165 modules 10 active ...ibrary/modules/_add-to-unscop 28% building modules 155/166 modules 11 active ...core-js/library/modules/_iter 28% building modules 155/167 modules 12 active ...ore-js/library/modules/_to-io 28% building modules 155/168 modules 13 active ...-js/library/modules/_property 28% building modules 155/169 modules 14 active ...es/core-js/library/modules/_s 28% building modules 155/170 modules 15 active ...dules/core-js/library/modules 28% building modules 155/171 modules 16 active ...ore-js/library/modules/_to-in 28% building modules 155/172 modules 17 active ...s/core-js/library/modules/_de 28% building modules 155/173 modules 18 active .../core-js/library/modules/_red 28% building modules 155/174 modules 19 active ...re-js/library/modules/_iter-c 28% building modules 155/175 modules 20 active ...ore-js/library/modules/_objec 28% building modules 155/176 modules 21 active ...dules/core-js/library/modules 28% building modules 155/177 modules 22 active ...es/core-js/library/modules/_i 28% building modules 155/178 modules 23 active ...ules/core-js/library/modules/ 28% building modules 155/179 modules 24 active ...ore-js/library/modules/_dom-c 28% building modules 155/180 modules 25 active ..._modules/setimmediate/setImme 28% building modules 156/180 modules 24 active ..._modules/setimmediate/setImme 28% building modules 157/180 modules 23 active ..._modules/setimmediate/setImme 28% building modules 158/180 modules 22 active ..._modules/setimmediate/setImme 29% building modules 159/180 modules 21 active ..._modules/setimmediate/setImme 29% building modules 160/180 modules 20 active ..._modules/setimmediate/setImme 29% building modules 161/180 modules 19 active ..._modules/setimmediate/setImme 29% building modules 162/180 modules 18 active ..._modules/setimmediate/setImme 29% building modules 163/180 modules 17 active ..._modules/setimmediate/setImme 29% building modules 164/180 modules 16 active ..._modules/setimmediate/setImme 29% building modules 165/180 modules 15 active ..._modules/setimmediate/setImme 29% building modules 166/180 modules 14 active ..._modules/setimmediate/setImme 30% building modules 167/180 modules 13 active ..._modules/setimmediate/setImme 30% building modules 168/180 modules 12 active ..._modules/setimmediate/setImme 30% building modules 169/180 modules 11 active ..._modules/setimmediate/setImme 30% building modules 170/180 modules 10 active ..._modules/setimmediate/setImme 30% building modules 171/180 modules 9 active ..._modules/setimmediate/setImmed 30% building modules 172/180 modules 8 active ..._modules/setimmediate/setImmed 30% building modules 173/180 modules 7 active ..._modules/setimmediate/setImmed 30% building modules 174/180 modules 6 active ..._modules/setimmediate/setImmed 31% building modules 175/180 modules 5 active ..._modules/setimmediate/setImmed 31% building modules 176/180 modules 4 active ..._modules/setimmediate/setImmed 31% building modules 177/180 modules 3 active ..._modules/setimmediate/setImmed 31% building modules 178/180 modules 2 active ..._modules/setimmediate/setImmed 31% building modules 179/180 modules 1 active ..._modules/setimmediate/setImmed 31% building modules 180/181 modules 1 active ...rary/modules/_object-keys-inte 31% building modules 180/182 modules 2 active ...-js/library/modules/_enum-bug- 31% building modules 180/183 modules 3 active ...-js/library/modules/_object-cr 31% building modules 180/184 modules 4 active ...ore-js/library/modules/_shared 31% building modules 181/184 modules 3 active ...ore-js/library/modules/_shared 31% building modules 182/184 modules 2 active ...ore-js/library/modules/_shared 31% building modules 183/184 modules 1 active ...ore-js/library/modules/_shared 32% building modules 184/185 modules 1 active ...js/library/modules/_array-incl 32% building modules 184/186 modules 2 active ...ore-js/library/modules/_object 32% building modules 185/186 modules 1 active ...ore-js/library/modules/_object 32% building modules 186/187 modules 1 active ...library/modules/_to-absolute-iHash: c0ed85915ae797d67bf5                    
Version: webpack 3.12.0
Time: 11363ms
                                                  Asset       Size  Chunks             Chunk Names
                                    mediamanager.min.js     198 kB       0  [emitted]  main
    ./../../../media/com_media/css/mediamanager.min.css    14.7 kB       0  [emitted]  main
                                mediamanager.min.js.map    1.47 MB       0  [emitted]  main
./../../../media/com_media/css/mediamanager.min.css.map  128 bytes       0  [emitted]  main
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1033 packages from 1858 contributors and audited 8148 packages in 122.129s
found 10 vulnerabilities (9 low, 1 high)
  run `npm audit fix` to fix them, or `npm audit` for details
astrid@astrid-TravelMate-5760G:/var/www/html/joomla-cms$ 

```

Nach dem erfolgreichen Ausführen von `composer install` und `npm install` kann nun auch im Browser 
die Installationsaufforderung von Joomla 4 über die Eingabe von `http://localhost/joomla-cms` in die Adresszeile des Browsers 
aufgerufen werden.

![Joomla Start Seite](../../media/5_Joomla_Web_Installer.png)




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
[^10]: https://git-scm.com/docs/git-stash
[^11]: https://git-scm.com/docs/git-clean
[^12]: https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment/de