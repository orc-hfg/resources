# Einstiegspunkte
> November 2025

Madek ist ein medienbasiertes System, ein Record besteht aus einem *Medieneintrag*. Zugleich bietet es mit *Sets* die Möglichkeit, einzelne Records zu verknüpfen und zu organisieren. In unserer täglichen Arbeit an der Hochschule für Gestaltung haben wir es fast ausschließlich mit Projekten zu tun. Projekte bestehen aus projektbezogenen Metadaten (Titel, Beschreibung, Ort, beteiligte Personen usw.) und mehreren Medieneinträgen (Fotos, Videos usw.). Diese Struktur lässt sich sehr gut mit Sets erfassen. De facto bilden daher Sets für uns den "Record". 

## Sets

Die Datenstruktur von Madek lässt sich als vernetztes Archivsystem beschreiben, in dem Sets als logische Sammlungen oder Gruppierungen von Medieneinträgen fungieren, ähnlich wie Tags, Playlists oder thematische Sammlungen, nicht wie klassische Ordner.

Ein Medieneintrag (z. B. ein Foto, Video, Dokument) kann in mehreren Sets gleichzeitig vorkommen. Sets enthalten keine Objekte exklusiv, sondern stellen Beziehungen (Verknüpfungen) zu ihnen her. Dadurch entsteht keine hierarchische Baumstruktur (wie bei Ordnern), sondern eher ein Netzwerk von Beziehungen, also eine semantische oder relationale Struktur.

Diese Architektur ermöglicht mehrdimensionale Sortierungen und Zusammenhänge, z. B. nach Thema, Projekt, Person, Ort usw., ohne Daten zu duplizieren.

Ein Set ist eine relationale Gruppierung, keine Containerstruktur. 

### Der halbe Graph

Im Grunde beschreibt die Set-Logik (Mengen-Logik) den halben Weg zum Graph-Modell: Man könnte Sets und Medieneinträge als Knoten in einem Graphen betrachten. Beziehungen wie *enthält*, *ist Teil von*, *verweist auf* würden dann als Kanten modelliert. Auf diese Weise ließen sich hierarchische *und* nicht-hierarchische Beziehungen parallel abbilden. Da aber das System keine explizite Kanten-Logik unterstützt (also keine eigene Datenstruktur für Relationen zwischen Objekten), lassen sich Graph-Beziehungen nicht abbilden. Madek basiert technisch auf einer objektrelationalen PostgreSQL-Datenbank.

Eine Möglichkeit könnte sein, semantische Graph-Beziehungen teilweise herzustellen, indem die Bestandteile eines Projekts auf ihr Projekt-Set explizit verweisen (quasi "bottom-up"). Aber 1. ist eine solche Referenzierung aktuell (November 2025) technisch nicht verfügbar, 2. wäre es aus redaktioneller Sicht mühsam und fehleranfällig, da jeder Bestandteil (Set, Medieneintrag) individuell mit dem Projekt-Set verknüpft werden müsste; natürlich müsste auch das User Interface die Arbeit mit Referenzierungen unterstützen (UX Design).

## Projekte

Wie gesagt, arbeiten wir hauptsächlich mit Projekten. Dabei zeigt sich eine Schwierigkeit der ausschließlich relationalen Beziehung: *Inhaltlich* betrachtet sind Projekte hierarchisch organisiert:

- Projekt-Set
  - Medieneintrag 1
  - Medieneintrag 2
  - Sub-Set (bspw. "Ausstellungsansichten")
    - Medieneintrag 1
    - Medieneintrag 2

Ohne Kennzeichnung von Projekt-Sets weiß das System nicht, ob ein Set ein Projekt (eine abgeschlossene inhaltliche Einheit), einen Teilbereich innerhalb eines Projekts oder etwas ganz anderes beschreibt.

Auch projektbezogene Anwendungen, die Daten über die API von Madek abrufen und weiterverarbeiten, behandeln alle Sets gleichrangig. Die Differenzierungen auf semantischer Ebene sind nicht verfügbar. Wir entwickeln zwei solcher Anwendungen: Project Uploader (Input-Modul) und Schaufenster (Output-Modul).

## Der Projekt-Anker

Unsere Lösung ist folgende: Wir realisieren ein Hybridmodell und führen über die Metadaten eine semantische Unterscheidungsebene innerhalb der bestehenden Set-Logik ein, ohne die technische Grundlage (also das relationale Set-Modell) zu verändern. 

Das technische Metadatum `settings:is_node` dient als Marker, um Sets mit besonderer semantischer Rolle zu kennzeichnen:

`is_node = true` → Das Set repräsentiert einen Einstiegspunkt (ein Projekt-Anker).  
`is_node = false` → Das Set ist "bloß" eine thematische oder technische Sammlung, kein Einstiegspunkt.

Damit entsteht innerhalb des flachen Set-Universums eine Schicht von *Pseudo-Knoten*, die als Einstiegspunkte bzw. Oberstrukturen fungieren. Diese Pseudo-Knoten bilden die "Wurzelknoten" eines Graphen nach, wobei die Kanten (Beziehungen) weiterhin nur implizit existieren.

Auf diese Weise lassen sich Projekte über `is_node == true` differenziert abfragen, filtern oder auflisten. Projekthierarchien oder -kontexte können im Frontend oder bei der Auswertung gezielt sichtbar gemacht werden. "Normale" Sets funktionieren weiterhin unverändert.
