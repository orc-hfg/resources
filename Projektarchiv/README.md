# Felder für Sprachen standardisieren

## Ausgangslage
Die Felder `creative_work:film_subtitle` und `creative_work:language` waren offene Keyword-Felder, das heißt unkontrollierte Listen. User konnten eigene Einträge machen. Die Folge waren nicht standardisierte und also nicht maschinenlesbar oder übertragbare Einträge, zudem Doubletten.

## Ziele
- Kontrollierte Liste
- Standardisierte Codierungen (Maschinenlesbarkeit)
- Optionen für menschliche User ohne weitere Erklärung verständlich

## 1. Kontrollierte Listen
Kontrollierte Listen sind in Madek über eine Einstellung im Admin-Bereich zu erreichen.

✅ Die Felder wurden geschlossen und können seitdem nur noch von Administratoren erweitert werden, nicht mehr von Usern.

## 2. Standardisierte Sprach-Codierung

In unserem Fall müssen wir die Sprache abbilden aber auch Dialekte, die nicht standardkonform über Sprachcodierungen verfügbar sind. Beispielsweise existiert in der Datenbank bereits ein Eintrag für "Badisch".

Außerdem ist das Metadaten-Schema von Madek insofern eigen, dass es weder Mehrsprachigkeit unterstützt (Standard-Sprache Deutsch) noch Taxonomie oder Ontologien.

Schließlich soll das System anwender*innenfreundlich und die verfügbaren Optionen im Interface des Projektarchivs ohne weitere Erklärung verständlich sein.

### Unser Schema

✅ Wir verwenden eine hybride Schreibweise: Deutsche Sprachbezeichnung mit ISO 639-2/T in Klammern.  
Optional: Spezifizierung mit ISO 3166 ALPHA-2 oder dem Namen eines Dialekts.

Beispiele:

- Deutsch (deu)
- Deutsch (deu-Badisch)
- Englisch (eng)
- Englisch (eng-GB)
- Englisch (eng-US)
- Esperanto (epo)

Damit ist Maschinenlesbarkeit prinzipiell möglich, menschliche Lesbarkeit und Verständlichkeit ohne weitere Hilfe ebenso, und das Schema ist flexibel genug, um nicht-standardkonforme Dialekte zu erfassen.

## Recherche

### ISO 639-2
- Dreistelliger Sprachcode (z. B. ger oder deu für Deutsch, eng für Englisch, fra für Französisch).
- Wird u. a. in Bibliotheken, Archiven und Museen häufig genutzt.
- Offiziell von der Library of Congress gepflegt.
- Anwendung z. B. in MARC21, EAD (Encoded Archival Description), Dublin Core und ISAD(G)-basierten Systemen.

ISO 639-3 erweitert ISO 639-2 auf alle bekannten Sprachen weltweit, auch Minderheitensprachen; wird zunehmend in digitalen Archivinformationssystemen verwendet, wenn eine genauere Sprachdifferenzierung nötig ist.

#### B-Codes: Bibliographic / ISO 639-2/B (ger, fre, gre)
- Bibliotheken (z. B. nach MARC 21, RDA, Dublin Core)
- Archive und Museen (z. B. bei EAD, ISAD(G), LIDO)
- kompatibel zur Library of Congress und historisch im Katalogstandard verankert

#### T-Codes: Terminologic / ISO 639-2/T (deu statt ger)
- neuere Systeme (v. a. mit Linked-Data-Anbindung, RDF, oder ISO 639-3-Kompatibilität)

### Dialekte

#### ISO 639-3 (Sprachcodes für Einzelsprachen):

Diese Norm vergibt eindeutige Codes (z. B. deu für Deutsch, gsw für Schweizerdeutsch). Manche Dialekte, die stark abweichen, haben eigene Codes (z. B. gsw = Alemannisch, bar = Bairisch). Andere Dialekte gelten als Teil einer Makrosprache (z. B. ara = Arabisch, mit vielen Dialekten, die keinen eigenen Code haben).

#### ISO 639-6 (Varietäten und Dialekte):

Diese Norm (noch kaum verbreitet) zielt speziell auf feingranulare Varietäten, Dialekte und Unterdialekte ab. Sie kann regionale Varianten von Sprachen abbilden (z. B. Bairisch vs. Schwäbisch). Der Standard ist aber nicht breit implementiert und wird selten in Software oder Datenbanken genutzt.

#### Linguistische Kataloge und Forschungsprojekte

a) Glottolog

Eine der präzisesten offenen Datenbanken für Sprach- und Dialektklassifikation. Jeder Dialekt bekommt einen eindeutigen Glottocode (z. B. bair1283 für Bairisch). Glottolog beschreibt auch genealogische Beziehungen (z. B. „Bairisch ist ein Dialekt des Hochdeutschen“).

b) Ethnologue

Nutzt ISO 639-3-Codes, ergänzt aber beschreibende Informationen über Dialekte innerhalb einer Sprache (z. B. „Deutsch hat Dialekte: Alemannisch, Bairisch, etc.“). 

c) WALS (World Atlas of Language Structures)

Erfasst Dialekte eher indirekt, indem es bestimmte sprachliche Merkmale (Phonologie, Grammatik) geografisch kartiert.

#### Praktische Standardisierung in digitalen Anwendungen

a) IETF Language Tags (BCP 47):

Dienen z. B. in Software, Webseiten und Übersetzungsdatenbanken. Aufbau: Sprache-Region-Variante, etwa:

- de-AT → Deutsch (Österreich)
- de-CH → Deutsch (Schweiz)
- gsw-CH → Schweizerdeutsch (Schweiz)

Damit können Dialekte technisch erfasst werden, ohne neue ISO-Sprachcodes zu schaffen.

**Das Problem in unserem Fall: zu unflexibel.**

"Badisch" ist innerhalb der ISO-639-Norm nicht definiert, sondern nur „deu“ (Deutsch). Es gibt keine eigenen Codes für regionale Varianten wie Schwäbisch, Pfälzisch, Fränkisch oder eben Badisch. 

b) CLDR (Unicode Common Locale Data Repository):

Enthält standardisierte Sprach- und Regionsvarianten, z. B. für Lokalisierungen (Datum, Währung, Schreibweise). Wird von großen Plattformen wie Google oder Apple verwendet.

### Links
https://www.loc.gov/standards/iso639-2/php/code_list-txt.php  
https://de.wikipedia.org/wiki/Liste_der_ISO-639-2-Codes
