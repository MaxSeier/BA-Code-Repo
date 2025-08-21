## Vorbereitung: Excel-Dateien oeffnen
- Excel: oeffne Datei [Staedte-Liste] -> ExcelInstance
- Excel: oeffne Datei [Wetter-Ergebnisse] -> ExcelInstance2

## Staedte aus der Liste einlesen
- Excel: Lese Spalte A (Zeilen 1-10) -> Variable ExcelData
- Excel: Schliesse [Staedte-Liste]

## Browser starten
- Firefox: Starte Browser mit URL "https://www.google.com"

## Hauptschleife: Fuer jede Stadt in ExcelData
- LOOP ueber ExcelData:
    - Gehe zu Google-Suche mit Query = "Wetter + <Stadt>"
    - Extrahiere Wetterdaten (Temperatur, Hoechst-/Tiefstwerte, Wetterlage, etc.)
    - Schreibe Ergebnisse in [Wetter-Ergebnisse] (Spalten B-H)

    ## Regelbasierte Bewertung der Temperatur
    - SWITCH Temperatur:
        - <=  -39   -> "sehr kalt"
        - <   -26   -> "kalt"
        - <   -13   -> "kuehl"
        - <   0     -> "leicht kuehl"
        - <   20    -> "behaglich"
        - <   26    -> "leicht warm"
        - <   32    -> "warm"
        - <   38    -> "heiss"
        - sonst     -> "sehr heiss"
    - Ergebnis in Spalte I
    - Schreibe Niederschlag in Spalte J
    - Screenshot der Wetteranzeige machen und in Tabelle einfuegen
- END LOOP

## Abschluss
- Schliesse Browser
- Speichere Wetter-Ergebnisse unter neuem Dateinamen (inkl. Zeitstempel)
