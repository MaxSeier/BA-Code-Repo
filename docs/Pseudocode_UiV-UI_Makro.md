## Initialisierung
- Setze Variablen:
  - Browser-Pfad (Firefox)
  - Staedte-Datei (staedte.xlsx)
  - Ergebnis-Template (wetter_ergebnisse_man.xltx)
  - Google-Such-URL
  - Speicherpfad & Dateiname
  - Startwerte fuer Schleifen (i = 1, row_counter = 3)
  - Bildschirmkoordinaten fuer Screenshots

## Vorbereitung
- Oeffne Firefox und ordne Fenster links an
- Oeffne Excel-Datei [staedte.xlsx]
  -> Gehe zu A2, markiere alle Staedte
  -> Kopiere in Zwischenablage
  -> Schliesse Datei
- Oeffne Excel-Template [wetter_ergebnisse_man.xltx]
  -> Ordne Fenster rechts an
  -> Fuege Staedte ab Zelle C3 ein

## Hauptschleife (fuer jede Stadt, solange i <= 9)
1. Hole Stadtname aus Ergebnis-Tabelle (Spalte C, aktuelle Zeile)
2. Wechsel zum Browser:
   - Google-Suche "Wetter <Stadt>"
   - Warte auf Google Widget
3. Extrahiere Wetterdaten:
   - Datum, Regenwahrscheinlichkeit, Luftfeuchtigkeit, Windgeschwindigkeit,
     Temperatur, Wetterzustand, Warnungen
4. Erstelle Screenshot (Snipping Tool, Bereichsauswahl per Koordinaten)
5. Verarbeite Rohwerte:
   - Extrahiere reine Zahlen aus Regenwahrscheinlichkeit, Luftfeuchtigkeit, Windgeschwindigkeit
6. Zurueck zu Excel:
   - Schreibe extrahierte Daten in die aktuelle Zeile
   - Temperatur interpretieren:
       - <= -39   -> "sehr kalt"
       - <  -26   -> "kalt"
       - <  -13   -> "kuehl"
       - <  0     -> "leicht kuehl"
       - <  20    -> "behaglich"
       - <  26    -> "leicht warm"
       - <  32    -> "warm"
       - <  38    -> "heiss"
       - sonst    -> "sehr heiss"
   - Warnungen eintragen
   - Screenshot einfuegen
7. Inkrementiere Zaehler (i + 1, row_counter + 1)

## Abschluss
- Erzeuge Zeitstempel
- Speichere Excel-Ergebnisdatei:
  * Dateiname = wetter_ergebnisse_uiv_${Zeitstempel}
  * Speicherort = definiertes Verzeichnis
- Schliesse Excel und Browser
