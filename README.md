# Seidemann Web GmbH - Testaufgaben

## 1.) Aufgabe

Installiere Dir eine frische OXID eShop Instanz der 6.5er-Serie auf Deinen lokalen Rechner.

Verwende Deine bevorzugte Variante, um Dir eine OXID eShop Instanz aufzusetzen.

Nutze beim Setup im Webbrowser die Demodaten.

-------------------------------------------------------------------------------------------------------------------------------
- Hint: Beachte die Systemvoraussetzungen. 
-------------------------------------------------------------------------------------------------------------------------------

Es gibt unterschiedliche Varianten sich eine lokale Entwicklungsumgebung aufzusetzen z.B.

- DDEV (Docker muss installiert sein + DDEV installieren)
- und viele Varianten mehr

Quellen:
- https://docs.oxid-esales.com/developer/en/6.5/getting_started/installation/index.html
- https://ddev.readthedocs.io/en/stable/
- https://ddev.readthedocs.io/en/stable/users/install/docker-installation/#docker-installation-linux
- https://docs.docker.com/engine/install/debian/
- https://ddev.readthedocs.io/en/stable/users/install/ddev-installation/#debianubuntu

-------------------------------------------------------------------------------------------------------------------------------
- Hint: Für die Docker-Umgebung nutze ich gerne DDEV.
-------------------------------------------------------------------------------------------------------------------------------

Beispiel:

```
mkdir ClientProjects
cd ClientProjects
mkdir oxid.seidemann.dev
cd oxid.seidemann.dev
ddev config --project-name="oxid.seidemann.dev" --project-type="php" --docroot="oxid/source" --webserver-type="apache-fpm" --php-version="8.1" --composer-version="2"
ddev start
ddev ssh
rm -rf oxid/
# composer self-update 2.7.9
composer create-project --no-dev oxid-esales/oxideshop-project oxid dev-b-6.5-ce
```

MariaDB Zugangsdaten DDEV:

Server: db
Benutzer: db
Passwort: db
Datenbank-Name: db

## 2.) Aufgabe

Ziel ist es eines der Standard Themes Wave oder Flow mit einem eigenen Child-Theme zu erweitern.

-------------------------------------------------------------------------------------------------------------------------------
- Hint: Nutze die OXID Developer Dokumentation.
-------------------------------------------------------------------------------------------------------------------------------

2a.) Lege die Verzeichnisstruktur Deines Child-Themes an.

Beispiel:

```
ddev start
ddev ssh
cd oxid/
mkdir source/Application/views/seidemannstore
touch theme.php
mkdir source/out/seidemannstore
cp seidemannweb.jpg source/out/seidemannstore/theme.jpg
```

2b.) Verändere mithilfe des Child-Themes die Produktdetailseite.

Die Produktdetailseite soll designtechnisch sich am Vorbild des Shopy Themes https://demo.htmlhunters.com/shopy/product.html orientieren.

Lade Dir dazu die 3 Produktbilder herunter und lege ein neues Produkt an um Deine Designanpassungen zu testen.

Anbei habe ich Dir zwei Screenshots vom Ist- und Soll-Stand des Layouts beigefügt.

Ziel ist es auf der Desktop-Ansicht die Platzierungen der Inhaltselemente zu ändern, dass die Beschreibung und Bewertung Tabs sich wie
im Soll-Stand auf der rechten Seite befinden.

Die Beschreibung und Bewertung soll wie im Soll-Stand ausklappbar sein.

Orientiere Dich beim Design an das Bootstrap CSS Framework für die Design-Elemente wie z.B. das Ausklappen der Beschreibung und Bewertung.

Quellen:
- https://docs.oxid-esales.com/developer/en/6.5/
- https://docs.oxid-esales.com/developer/en/6.5/development/modules_components_themes/theme/index.html
- https://docs.oxid-esales.com/developer/en/6.5/development/modules_components_themes/theme/theme_via_composer.html
- https://www.the-real-world.de/oxid6-child-themes-auf-basis-von-wave-parent-erstellen/
- https://getbootstrap.com/
- https://themes.getbootstrap.com/product/shopy/
- https://demo.htmlhunters.com/shopy/product.html

## 3.) Aufgabe

Die Hauptnavigation soll um eine neue Landingpage namens "Filiale" ergänzt werden. 

Auf dieser Landingpage soll eine Karte von YellowMap mit der Anschrift der Seidemann Web GmbH eingebunden werden.

Schau Dir die Quellenangabe von YellowMap mit der Anleitung an und überlege wie Du den JavaScript-Code und HTML-Code einbindest.

Ein API-Key erhältst Du über die kostenfreie Registrierung unter https://www.smartmaps.net/ 

Ein Screenshot wie es später im Frontend Deines Demo-Shops aussehen soll mit der Karteneinbindung ist diesem Repository beigefügt.

Nutze gerne die ganze Breite aus, der Screenshot ist ein Beispiel zur Verdeutlichung der Anforderung.

-------------------------------------------------------------------------------------------------------------------------------
- Hint: Prüfe, ob sich die Anforderung "ohne" Modul lösen lässt oder ob Du lieber Dein Child-Theme SeidemannStore erweiterst.
-------------------------------------------------------------------------------------------------------------------------------

Quellen:
- https://docs.oxid-esales.com/developer/en/6.5/development/modules_components_themes/module/index.html
- https://www.yellowmap.com/
- https://docs.yellowmap.com/howto/
- https://docs.yellowmap.com/smartmaps-javascript/anleitung/erste-schritte/
- https://www.smartmaps.net/

## 4.) Aufgabe (Optional)

Da wir neben OXID eShop auch mit Shopware arbeiten, wäre das Ziel dieser Aufgabe eine lokale Shopware Community Edition Instanz
bei Dir Lokal auf Deinen Rechner zu installieren.

Verwende Deine bevorzugte Variante, um Dir eine Shopware Instanz aufzusetzen.

Nutze beim Setup im Webbrowser die Demodaten.

PayPal Konfiguration kann übersprungen werden.

Erweiterungen Empfehlungen können ebenfalls übersprungen werden mit "Weiter".

Shopware Account und Shopware Store kann übersprungen werden.

-------------------------------------------------------------------------------------------------------------------------------
- Hint: Beachte die Systemvoraussetzungen. 
-------------------------------------------------------------------------------------------------------------------------------

Es gibt unterschiedliche Varianten sich eine lokale Entwicklungsumgebung aufzusetzen z.B.

- Devenv
- Dockware
- Symfony Flex (seit 6.5.*)
- DDEV (Docker muss installiert sein + DDEV installieren)
- und viele Varianten mehr

Beispiel:

```
mkdir ClientProjects
cd ClientProjects
mkdir shopware.seidemann.dev
cd shopware.seidemann.dev
ddev config --project-name="shopware.seidemann.dev" --project-type="php" --docroot="shopware/public" --webserver-type="apache-fpm" --php-version="8.3" --composer-version="2"
ddev start
ddev ssh
rm -rf shopware/
composer create-project shopware/production shopware
```

Quellen:
- https://developer.shopware.com/docs/guides/installation/
- https://developer.shopware.com/docs/guides/installation/requirements.html
- https://www.matthias-zeis.com/shopware-6/programmieren-lernen-links-tipps-tutorials/symfony-flex-recipe
- https://ddev.readthedocs.io/en/stable/
- https://ddev.readthedocs.io/en/stable/users/install/docker-installation/#docker-installation-linux
- https://docs.docker.com/engine/install/debian/
- https://ddev.readthedocs.io/en/stable/users/install/ddev-installation/#debianubuntu
