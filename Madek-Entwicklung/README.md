# Madek Entwicklung

`11.08.2022`

Langfristig wollen wir Madek als nachhaltige, community-driven Software etablieren. Darin besteht ein wichtiger Aspekt des Netzwerks mit Partnerinstitutionen, das wir aufbauen.  

Bei der Softwareentwicklung liegt unser Schwerpunkt auf Aspekten der Medienplattform wie user interaction und Modularisierung der Software.  

Unser wichtigstes Ziel ist es, dass die Redaktionsoberfläche (WebApp) flexibel an das System angebunden ist. Dazu soll eine [Input API](#Erweiterung-der-API) (lesen, schreiben, verändern, löschen) entwickelt werden (bzw. eine zusätzliche Kommunikationsschicht zwischen Datenbank und Frontend/WebApp). Über diese können unterschiedliche Interfaces (oder auch Services) mit der Datenbank und dem Dateisystem kommunizieren.  

Aufbauend auf der neuen API wollen wir ein neues [Interface](#Interface-WebApp) für die Redaktionsoberfläche entwickeln.  

&nbsp; 

## Erweiterung der API
`HfG` `Community` `ZHdK`

### API
Unser Ziel ist eine API, die es Madek ermöglicht,
1. verschiedene Benutzeroberflächen (WebApp) auf modulare Weise anzubinden,
2. die Software in Pipelines und Workflows mit anderen Systemen zu integrieren,
3. strukturierte Daten zu importieren (aus Listen),
4. externe Datenbanken wie Normdatenbanken und Vokabulare anzubinden.

### Dokumentation
1. technische Dokumentation der neu entwickelten API für Entwickler
2. Hands-on-Dokumentation der Abfrage-API. Inhalte aus Madek sollen ohne höhere technische Kenntnisse in Websites (CMS) eingebunden werden können. Anleitungen und Beispiele der API-Anfragen in gängigen Web-Entwicklungssprachen (PHP, JavaScript).

### In Madek verwendete Techniken
Relationale DB PostgreSQL, JVM, Clojure, REST und GraphQL, Ruby on Rails (eher legacy status), Ansible, React, ClojureScript mit Reagent.

&nbsp;

## Interface WebApp
`HfG` `Community`

Die Entwicklung einer neuen Redaktionsoberfläche gliedert sich in drei Teile: Konzeption, Design und Umsetzung.

### Konzeption
Parallel zur neuen API wird die abstrakte Konzeption des Interfaces entwickelt: Architektur, Funktionen, Abläufe. Framework?
- Systematik bzw, Wireframes
- ggf. Prototyping

### Design: UX/UI
Auf der Basis der Konzeption wird ein konkreter Prototyp entworfen.  
UX: interaction design, usability, Benutzerfreundlichkeit, etc.  
UI: visuelle Gestaltung der Redaktionsoberfläche (user interface), Layout, Farben, Typographie, etc.

### Umsetzung: Frontend-Entwicklung
Umsetzung/Programmierung des Designs in einem noch zu definierenden Framework (Vue, React, Svelte, Ruby on Rails, etc.).

&nbsp; 


## Authentifizierung
`HfG` `Community`

- LDAP-Anbindung
- oAuth

&nbsp;


## Schnittstelle zu anderen Datenbanken und Systemen
`HfG` `Community`

- Nextcloud, Moodle
- Normdatenbanken, Vokabulare

&nbsp;

## Importieren von strukturierten Daten (Listen)
`HfG` `Community` `ZHdK`

Eine Lösung, um in Listen erfasste Daten nach Madek zu importieren. 

&nbsp;

## Medienkonvertierung

`HfG` `Community`

Madek nutzt den kostenpflichtigen Service *Zencoder* für die Video-Codierung. Probleme:
- Datenschutz
- Abhängigkeit
- zusätzlicher Traffic
- Kosten

https://www.brightcove.com/de/products/zencoder/  
https://zencoder.support.brightcove.com/

Präferenz: Konvertierung auf Madek-Serverumgebung als default, Services optional zuschaltbar.  
Alternative zu Zencoder.

&nbsp;

## Sonstiges, to discuss

### Entites erweitern
`HfG` `Community`

Aktuell existiert in Madek [Entities bezogen auf Personen](https://madek.readthedocs.io/en/latest/architecture/): `user`, `person`, `group`. Nützlich wäre zusätzlich, das Vorlesungsverzeichnis über eine Entity abzubilden, etwa `Veranstaltung` im Sinne von Vorlesung/Seminar. 

Entities befinden sich systematisch auf einer anderen Ebene als Medieneinträge und Sets. 

# ## Alternative API
`HfG` `Community`

- GraphQL

### Medienformate
`HfG` `Community`

- Modularisierung
- weitere Medienformate

### Dokumentation erweitern
`HfG` `Community`

- technische Dokumentation ausbauen bzw. überarbeiten
- allgemeine User-Dokumenation erstellen (Dokumentation der ZHdK als Ausgangspunkt)
- konkrete Abläufe beschreiben (Cookbooks / How-Tos), ggf. mit Code-Snippets
- Installation (technische Dokumenation)

Technische Dokumentationen richten sich an Entwickler (technisches Verständnis der Software nötig). 

Anwender-Dokumentationen richten sich an Studierende und Mitarbeiter\*innen, die mit Madek arbeiten (Verständnis sämtlicher Aspekte der Anwendung von Madek auf der Basis des neuen Interfaces). 

### Installationsskript vereinfachen
`Community`

Die Installation von Madek ist kompliziert und benötigt fortgeschrittenes IT-Wissen, das nicht in jeder Institution vorausgesetzt werden kann. Zudem ist das aktuelle Instalattionsskript offensichtlich in manchen Teilen für die Bedürfnisse der ZHdK optimiert. 

- Installation generell vereinfachen
- allgemeingültiges Installationsskript bzw. Modularisierung der Installation (wenn möglich)

### Session management neu aufbauen
`HfG` `Community` `ZHdK`

Beschrieben von Tom Schank am 12.07.2022 als Abhängigkeit in Zusammenhang mit der Input-API.
