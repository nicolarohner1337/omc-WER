## Aufgabenstellung
<b>Sprachenvielfalt Schweiz </b>-
Wie könnte das Verhältnis 
der Muttersprachen in der Schweiz 
im Jahre 2050 aussehen?

## Systemdefinition
- Die Erwartungswerte der Zufallsvariablen sind trivialerweise von der Bevölkerungsgrösse abhängig (je mehr Menschen, desto mehr Geburten, Todesfälle usw)
- Es wurden folgende Zufallsvariablen für die Sprachgruppen Deutsch, Französisch, Italienisch und Andere identifiziert:<br>
  - E<sub>s</sub>: Einwanderung nach Sprache<br>
  - A<sub>s</sub>: Auswanderung nach Sprache<br>
  - G<sub>s</sub>: Geburtenrate nach Sprache<br>
  - T<sub>s</sub>: Todesrate nach Sprache<br>
Die Ausprägungen der einzelnen Zufallsvariablen sind die jeweiligen Werte in einem bestimmten Jahr.<br>

# Lösungsstrategie
## Datenaufbereitung Zufallsvariablen:
Die Oben genannten Zufallsvariablen wurden aufgrund von Historischen Daten des BSF definiert.<br>

E: Die Einwanderung wurde anhand folgender Datenquelle definiert: je-d-01.05.04.01.01.xlsx Sheet: Einwanderungen<br>
Für die Einwanderungszahl nach Sprache wurde leider keine direkte Datenquelle gefunden.<br>
Statdessen wird angenommen, dass Einwanderungen aus bestimmten Ländern/Regionen zu unseren Sprachgruppen zugeordnet werden können.<br>
In dieser Tabelle sind die Einwanderungszahlen aus einzelnen Ländern vom Jahre 1991-2020 aufgeführt.<br>
Zuweisung Deutsch: "Schweizer", "Deutsche", "Österreicher"<br>
Zuweisung Französisch: "Franzosen"<br>
Zuweisung Italienisch: "Italiener"<br>
Zuweisung Andere: "Total" - Deutsch - Französisch - Italienisch<br>
<br>
A: Die Auswanderung wurde anhand folgender Datenquelle definiert: je-d-01.05.04.01.01.xlsx Sheet: Auswanderungen<br>
Für die Auswanderungszahl nach Sprache wurde leider keine direkte Datenquelle gefunden.<br>
Statdessen wird angenommen, dass Auswanderungen aus bestimmten Ländern/Regionen zu unseren Sprachgruppen zugeordnet werden können.<br>
In dieser Tabelle sind die Auswanderungszahlen aus einzelnen Ländern vom Jahre 1991-2020 aufgeführt.<br>
Zuweisung Deutsch: "Schweizer", "Deutsche", "Österreicher"<br>
Zuweisung Französisch: "Franzosen"<br>
Zuweisung Italienisch: "Italiener"<br>
Zuweisung Andere: "Total" - Deutsch - Französisch - Italienisch<br>
<br>
G: Die Geburenrate wurde anhand folgender Datenquellen definiert: je-d-01.08.01.02.xlsx, su-d-01.04.01.01.08.xlsx Sheet: Total<br>
Für die Geburtenrate nach Sprache wurde leider keine direkte Datenquelle gefunden.<br>
Deshalb wurde zuerst aus je-d-01.08.01.02.xlsx pro Kanton die Relative haufigkeit der einzelnen Sprachen berechnet.<br>
Dazu wurde die Zahl des Feldes "Anzahl Personen" der Sprachen "Deutsch (oder Schweizerdeutsch)", "Französisch (oder Patois Romand)", und Italienisch (oder Tessiner/Bündner-italienischer Dialekt) der Sprachen Deutsch, Französisch und Italienisch zugeordnet.<br>
Die übrigen Sprachen wurden zu Andere zugeornet.<br>
Nun hat man die Absolute Häufigkeit der einzelnen Sprachgruppen nach Kanton.<br>
Jetzt wurden die Anzahl der Sprachgruppen durch die Summe aller Sprachzahlen nach Kanton geteilt um auf die relative Häufigkeit zu schliessen.<br>
In einem zweiten Schritt wurde aus su-d-01.04.01.01.08.xlsx die Geburtenzahl nach Kanton pro Jahr extrahiert.<br>
Nun muss die relative Häufigkeit der Sprachgruppen nach Kanton pro Jahr mit der relativen Häufigkeit der Sprachen nach Kanton multipliziert werden.<br>
Nun erhält man die Geburtenrate nach Sprache und Kanton pro Jahr<br>
Anschliessend wurden die Zahlen nach Kanton addiert, damit nur noch die Geburtenrate nach Sprache und Jahr übrig bleibt.<br>
<br>
T: Die Todesrate wurde anhand folgender Datenquellen definiert: je-d-01.08.01.02.xlsx, su-d-01.04.02.01.14.xlsx Sheet: Total<br>
Für die Todesrate nach Sprache wurde leider keine direkte Datenquelle gefunden.<br>
Deshalb wurde zuerst aus je-d-01.08.01.02.xlsx pro Kanton die Relative haufigkeit der einzelnen Sprachen berechnet.<br>
Dazu wurde die Zahl des Feldes "Anzahl Personen" der Sprachen "Deutsch (oder Schweizerdeutsch)", "Französisch (oder Patois Romand)", und Italienisch (oder Tessiner/Bündner-italienischer Dialekt) der Sprachen Deutsch, Französisch und Italienisch zugeordnet.<br>
Die übrigen Sprachen wurden zu Andere zugeornet.<br>
Nun hat man die Absolute Häufigkeit der einzelnen Sprachgruppen nach Kanton.<br>
Jetzt wurden die Anzahl der Sprachgruppen durch die Summe aller Sprachzahlen nach Kanton geteilt um auf die relative Häufigkeit zu schliessen.<br>
In einem zweiten Schritt wurde aus su-d-01.04.02.01.14.xlsx die Todesrate nach Kanton pro Jahr extrahiert.<br>
Nun muss die relative Häufigkeit der Sprachgruppen nach Kanton pro Jahr mit der relativen Häufigkeit der Sprachen nach Kanton multipliziert werden.<br>
Nun erhält man die Todesrate nach Sprache und Kanton pro Jahr<br>
Anschliessend wurden die Zahlen nach Kanton addiert, damit nur noch die Todesrate nach Sprache und Jahr übrig bleibt.<br>
<br>
<br>

## Wie wurden die Warscheinlichkeiten modelliert?
Die Warscheinlichkeiten der Ausprägungen wurden mittels python library "Fitter" mit der cost-function "sumsquare_error" ermittelt.<br>
Dazu wurde der Fitter über die Aufbereiteten Daten der Zufallsvariablen laufen gelassen und somit die am besten passende Verteilung mit den entsprechenden Parametern ermittelt.<br>
<br>
<br>

## Mit welcher Mehtode wird die Fragestellung beantwortet:
Die Fragestellung wird mittels Monte Carlo Siumulation beantwortet.<br>
Dazu wird für jede Sprachgruppe (Deutsch, Französisch, Italienisch, Andere) eine separate Simulation durchgeführt.<br>
N<sub>s,k</sub> = E<sub>s,N<sub>s,k-1</sub></sub> + G<sub>s,N<sub>s,k-1</sub></sub> - A<sub>s,N<sub>s,k-1</sub></sub> - T<sub>s,N<sub>s,k-1</sub></sub><br>
Der Erwartungswert und Varianz der einzelnen Zufallsvariablen wurde anhand von der berechneten population der Epoche k-1 abhängig gemacht (der Variationskoeffizient bleibt gleich).<br>
<br>
