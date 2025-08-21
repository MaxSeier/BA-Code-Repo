## Hauptstruktur
- FUNCTION Main
    - CALL Preparation
    - LOOP (i = 0 bis 8)
        - CALL Data Collection
    - END LOOP
    - CALL Follow-Up
- END FUNCTION

## Subflow: Preparation
- Oeffne Browser (Firefox, Startseite: Google)
- Oeffne Excel [Staedte-Liste]
    - Markiere Staedte (ab Zeile 2)
    - Kopiere in Zwischenablage
    - Schliesse Datei
- Oeffne Excel [Wetter-Ergebnisse]
- Fuege Staedte ein (ab Spalte C, Zeile 3)
- Fensteranordnung optimieren

## Subflow: Data Collection
- LOOP ueber jede Stadt (aus eingefuegter Liste):
    - Gehe im Browser zu Google
    - Suche: "Wetter <Stadt>"
    - Extrahiere und formatiere Wetterinformationen:
        * Temperatur (aktuell)
        * Max-/Min-Werte
        * Wetterzustand (z. B. sonnig, bewoelkt)
        * Niederschlag
    - Schreibe Ergebnisse in Excel (Spalten D-J)
    - Temperatur interpretieren:
        - <=  -39   -> "sehr kalt"
        - <   -26   -> "kalt"
        - <   -13   -> "kuehl"
        - <   0     -> "leicht kuehl"
        - <   20    -> "behaglich"
        - <   26    -> "leicht warm"
        - <   32    -> "warm"
        - <   38    -> "heiss"
        - sonst     -> "sehr heiss"
    - Screenshot der Wetteranzeige einfuegen
- END LOOP

## Subflow: Follow-Up
- Browser schliessen
- Ergebnisdatei mit Zeitstempel speichern
