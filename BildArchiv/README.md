# Bildarchiv
Das Modul kopiert bei Auslösung durch eine gewählte Variable ein Bild. Es ist einstellbar wieviele Bilder gespeichert werden sollen.

### Inhaltsverzeichnis

1. [Funktionsumfang](#1-funktionsumfang)
2. [Voraussetzungen](#2-voraussetzungen)
3. [Software-Installation](#3-software-installation)
4. [Einrichten der Instanzen in IP-Symcon](#4-einrichten-der-instanzen-in-ip-symcon)
5. [Statusvariablen und Profile](#5-statusvariablen-und-profile)
6. [WebFront](#6-webfront)
7. [PHP-Befehlsreferenz](#7-php-befehlsreferenz)

### 1. Funktionsumfang

* Auswählbares Quellbild und auswählbare Auslöservariable
* Einstellbare Anzahl von Bildern, welche gespeichert werden sollen
* Wenn eine Auslöservariable ausgewählt ist wird ein Ereignis erstellt, welches auf die Aktualisierung dieser reagiert
* Das Ereignis kann bis auf die Auslöservariable vollständig personalisiert werden
* Bilder bekommen den Zeitpunkt des Auslösens als Namen
* Bilder werden chronologisch von alt -> neu in der Kategorie Bilder angezeigt
* Automatisches Löschen der ältesten Bilder, beim Erreichen der eingestellten maximalen Bilderanzahl

### 2. Voraussetzungen

- IP-Symcon ab Version 4.2

### 3. Software-Installation

* Über den Module Store das Modul Bild-Archiv installieren.
* Alternativ über das Module Control folgende URL hinzufügen:
`https://github.com/symcon/BildArchiv`  

### 4. Einrichten der Instanzen in IP-Symcon

- Unter "Instanz hinzufügen" kann das 'Bildarchiv'-Modul mithilfe der Schnellsuche gefunden werden.  

__Konfigurationsseite__:

Name            | Beschreibung
--------------- | ---------------------------------
Bild            | Quellbild, welches kopiert werden soll
Anzahl          | Maximale Anzahl an Bildern, die gespeichert werden sollen
Auslösevariable | Variable bei deren Änderung das Quellbild ins Archiv kopiert werden soll 

### 5. Statusvariablen und Profile

Die Statusvariablen/Kategorien werden automatisch angelegt. Das Löschen einzelner kann zu Fehlfunktionen führen.

##### Statusvariablen

Name     | Typ       | Beschreibung
-------- | --------- | ----------------
Bilder   | Kategorie | Hier werden die Quellbilder hineinkopiert
AddImage | Ereignis  | Wird durch die Auslösevariable ausgelöst und stößt das Kopieren des Quellbildes an

##### Profile:

Es werden keine zusätzlichen Profile hinzugefügt

### 6. WebFront

Über das WebFront wird die Variable angezeigt. Es ist keine weitere Steuerung oder gesonderte Darstellung integriert.

Zur Darstellung der Bilder in der Kategorie "Bilderarchiv" kann ein Inhaltsteiler im WebFront hinzugefügt werden oder ein Link der Kategorie gemacht werden.  
Achtung: Es ist nicht nützlich direkt die Bilder aus dem Archiv zu verlinken, da sich durch die Aktualisierungen die ID's ändern.


### 7. PHP-Befehlsreferenz

`boolean BA_AddImage(integer $InstanzID);`  
Kopiert das aktuelle Quellbild in die Kategorie "Bilder" des Moduls "BildArchiv" mit der InstanzID $InstanzID.
Die Funktion liefert keinerlei Rückgabewert.  
Beispiel:  
`BA_AddImage(12345);`
