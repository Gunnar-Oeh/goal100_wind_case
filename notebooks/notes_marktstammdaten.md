## 1. Projekttreffen Goal 100

- Landräte: Via Wikipedia abfragen, ermöglicht evtl auch eine Historie des Wahlverhaltens
- wichtig welche Datenquellen für die Lücken, die das MaStdr nicht abdeckt (politische Verantwortlichkeiten)
- Klärung Unterschied Anlagen/Einheiten/Lokationen
- Zieldaten: Was sind die Zieldaten an denen gemessen wird
- Weitere Datenquellen: Projektierer, Hersteller
- Windvorrangflächen. Wie verändert sich das? Energieagenturen, Geodatenportale der Bundesländer

### 1.2 Herangehensweise von Zeit-Online
- Betreiber haben Eintragungspflicht für das MaStdr der BNetzA
- vollständiger Check findet durch die BNetzA nicht statt
- falsche Daten oftmals bei den Koordinaten
- Bereinigung durch das UFZ
- Erster Abfrageschritt -> befindet sich die Koordinate im entsprechenden Landkreis
- Lokationen?
- Zeitpunkte der Eintragung, eigentlich ab Planung, aber was heißt das?
- MaStdr triggert keine Prozesschritte
- Funktion: Überblick für die übergeordnete Netzagentur um die Stabilität des Netzes zu gewährleisten
- Kleinanlagen wurden via Leistung ab 500 kW herausgefiltert
- Meldeverzug von mehreren Wochen Frist
- gezeigt werden abgeschlossene Wochen
- Stichtag für Auktionen: vierteljährlich
- PostgreSQL-Datenbank aus R, python, Javascript-parsern
- Parser laufen per chronjob (workflow-orchestration) mit der API
- Daten werden überschrieben
- XML-API ist schlecht
- erweiterte Übersicht - seite untersuchen - filter zurechtsetzen. Muss anhand bestimmter IDs wiederholt werden
- Frage: Alle Daten in eine Zeitreihe überführen oder nur bestimmte
- Leistungsunterschiede, verschiedene Leistungskennwerte: bei Wind keine Unterscheidung zwischen Brutto und Netto. Netto wird eingetragen und in Brutto übertragen
- Netzanschluss in Prüfung -> wird Strom überhaupt eingespeist?
- Wie wird mit Repowering umgegangen - muss man sich durch den Standort und die Daten Stillegung selbst erschließen
    -> eröffnet Fragen zur Dauer zwischen Abschaltung und Repowering
- Zeit stellt den Zubau pro Bundesland wochenweise dar
- Abgleich mit den Ausbauzielen pro Bundesland: Über die entsprechenden Spalten
- Windvorrangflächen: von den Ländern
- Windeignungsflächen: UFZ/Bosch+Partner, Agora Energiewende
- Vergleich Potential/Vorrangflächen
- Genehmigung ist Teilnahmevorraussetzung für den Auktionsprozess
- fürs Frontend: DataWrapper SaaS, wenn was eigenes ansteht mit React. Ermöglicht Infrastruktur
- Von der Datenbank werden dann wiederum csv mit skripten generiert und hinterlegt bei DataWrapper
- Mapbox für aufwendigere Karten
- Kern-Ausgangspunkt: MaStdr, Potenzialflächen, Vorrangflächen, daraus verschneidbare
- Supabase ermöglicht gute verinfachte Nutzung der Datenbank für das Frontend (evtl muss keine ausdifferenzierte API geschrieben werden)
- Zwei Frontends - eines für die Öffentlichkeit, eines Intern

## Marktstammdatenregister

### Aufbau Gesamtdownload:
- Unterscheidung zwischen EinheitenWind.XML technische und geographische Daten zur Einheit
- und AnlagenEeg.XML: Infos zur Vergütung und Ausschreibung nach EEG

#### EinheitenWind.xml
- enthält Address, Geo- und Administrative Gebietszugehörigkeitsdaten, 
- Inbetriebnahme, Stillegung und auch temporäre Stilllegung
- Leistungswerte (Brutto/Netto)
- Technologie
- Naben/Rotorhöhe, Rotordurchmesser
- Auflagen zur Abschaltung
- Bürgerenergie
- Schlüssel: EinheitMastrNummer 

#### AnlagenEEGWind.xml
- geringere Anzahl an Spalten.
- Hauptsächlich Informationen zur Vergütung, Ausschreibung
- Schlüssel: EegMastrNummer

## Aufbau Datenbank
- nicht nur eine Tabelle der Einheit, sondern eine weitere für jede Einheit mit dem 