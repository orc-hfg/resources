# Madek Entwicklung

`16.08.2023`

Langfristig wollen wir Madek als nachhaltige, community-driven Software etablieren. Darin besteht ein wichtiger Aspekt des Netzwerks mit Partnerinstitutionen, das wir aufbauen.  

Bei der Softwareentwicklung liegt unser Schwerpunkt auf Aspekten der Medienplattform wie user interaction und Modularisierung der Software.  

Unser wichtigstes Ziel ist es, dass die Redaktionsoberfläche (WebApp) flexibel an das System angebunden werden kann. Dazu entwickeln wir eine CRUD API (lesen, schreiben, verändern, löschen), mit der unterschiedliche Interfaces und Services/Anwendungen mit Madek interagieren können.  

&nbsp; 

## Neue API

### Ziele
1. Verschiedene Benutzeroberflächen (WebApp) sollenn modular an Madek angebunden werden können.
2. Die Software soll in Pipelines und Workflows mit anderen Systemen integrierbar sein.
3. Strukturierte Daten sollen importierbar sein (Listen).
4. Externe Datenbanken wie Normdatenbanken und Vokabulare sollen angebunden werden können.

### Dokumentation
1. Technische Dokumentation der neu entwickelten API für Entwickler.
2. Hands-on-Dokumentation der Abfrage-API. Inhalte aus Madek sollen ohne höhere technische Kenntnisse in Websites (CMS) eingebunden werden können. Anleitungen und Beispiele der API-Anfragen in gängigen Web-Entwicklungssprachen (PHP, JavaScript).

### In Madek verwendete Techniken
Relationale DB PostgreSQL, JVM, Clojure, REST und GraphQL, Ruby on Rails (eher legacy status), Ansible, React, ClojureScript mit Reagent.

&nbsp;

## Interface WebApp

Aufgrund unterschiedlicher Entwicklungen haben wir unserer Strategie geändert. Anstatt einer vollständig neuen Benutzeroberfläche sollen Module für bestimmte Anwendungen entwickelt werden. Die aktuelle, "traditionelle" Madek-WebApp bleibt weiterhin parallel im Einsatz.

&nbsp; 

## Authentifizierung

Die Authentifizierungs-Methode in Madek wurde von der ZHdK neu geschrieben. Wir entwickeln ein Modul für die Anpassung an unsere internen Systeme (HfG).

&nbsp;

## Schnittstelle zu anderen Datenbanken und Systemen

Geplant sind Nextcloud, Moodle sowie Normdatenbanken und ggf. externe Vokabulare.

&nbsp;

## Importieren von strukturierten Daten (Listen)

Eine Lösung, um in Listen erfasste Daten nach Madek zu importieren. 

&nbsp;

## Videokonvertierung

Madek nutzt den kostenpflichtigen Service *Zencoder* für die Video-Codierung. Probleme:
- Datenschutz
- Abhängigkeit
- zusätzlicher Traffic
- Kosten

https://www.brightcove.com/de/products/zencoder/  
https://zencoder.support.brightcove.com/

Unsere Präferenz: 
- Konvertierung auf Madek-Serverumgebung als default, Services optional zuschaltbar.  
- Alternative zu Zencoder.

&nbsp;

## Medienservice

Der Medienservice in Madek muss neu geschrieben werden. Zusammenarbeit mit ZHdK ist erwünscht.

## Sonstiges, to discuss

<!-- 
### Entites erweitern
`HfG` `Community`

Aktuell existiert in Madek [Entities bezogen auf Personen](https://madek.readthedocs.io/en/latest/architecture/): `user`, `person`, `group`. Nützlich wäre zusätzlich, das Vorlesungsverzeichnis über eine Entity abzubilden, etwa `Veranstaltung` im Sinne von Vorlesung/Seminar. 

Entities befinden sich systematisch auf einer anderen Ebene als Medieneinträge und Sets.  

### Alternative API
`HfG` `Community`

- GraphQL
-->

### Medienformate

- Modularisierung des Medienservices (siehe oben)
- Madek soll weitere Medienformate unterstützen können

### Dokumentation erweitern

- technische Dokumentation ausbauen bzw. überarbeiten
- allgemeine User-Dokumenation erstellen (Dokumentation der ZHdK als Ausgangspunkt)
- konkrete Abläufe beschreiben (Cookbooks / How-Tos), ggf. mit Code-Snippets
- Installation (technische Dokumenation)

Technische Dokumentationen richten sich an Entwickler (technisches Verständnis der Software nötig). 

Anwender-Dokumentationen richten sich an Studierende und Mitarbeiter\*innen, die mit Madek arbeiten (Verständnis sämtlicher Aspekte der Anwendung von Madek auf der Basis des neuen Interfaces). 

### Installationsskript vereinfachen

Die Installation von Madek ist kompliziert und benötigt fortgeschrittenes IT-Wissen, das nicht in jeder Institution vorausgesetzt werden kann. Zudem ist das aktuelle Instalattionsskript offensichtlich in manchen Teilen für die Bedürfnisse der ZHdK optimiert. 

- Installation generell vereinfachen
- allgemeingültiges Installationsskript bzw. Modularisierung der Installation (wenn möglich)

### Session management neu aufbauen

Beschrieben von Tom Schank am 12.07.2022 als Abhängigkeit in Zusammenhang mit der Input-API.
