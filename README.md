# Wetterdaten Automatisierung

Dieses Repository enthält zwei Implementierungen desselben Automatisierungs-Szenarios:  
Das Auslesen von Wetterdaten für verschiedene Städte aus dem Web und die strukturierte Ablage in einer Excel-Datei.

## Inhalt

- `PA-API-Run/`  
  Enthält den Power Automate Desktop (PAD) Flow über die Excel-API in JSON-Form.  
  Struktur:  
  - `PA-API-Desktop-Flow_Main.json` – Hauptablauf  

- `PA-UI-Run/`  
  Enthält die Power Automate Desktop (PAD) Flows über die Excel-UI in JSON-Form.
  Struktur: `PA-UI-Desktop-Flow_...` 
  - `Main.json` – Hauptablauf 
  - `Preparation.json` – Vorbereitungsschritte (Excel öffnen, Städte einfügen etc.) 
  - `DataCollection.json` – Webscraping und Dateneintrag 
  - `FollowUp.json` – Speicherung und Schließen 

- `UiV-UI-Run/`  
  Enthält das Ui.Vision RPA Makro als einzelne JSON-Datei:  
  - `UiV-UI-Desktop-Makro.json`

- `docs/`  
  Enthält ergänzende Dokumentation, u.a. die vereinfachten Kurzfassungen im Pseudocode-Stil für den Anhang der Arbeit.

---

## Kurzbeschreibung der Flows

### Power Automate Desktop (PAD)
Der Ablauf ist modular in Subflows gegliedert:
1. **Main** – Orchestrierung, Aufruf der Subflows  
2. **Preparation** – Öffnet Excel, fügt Städte ein  
3. **Data Collection** – Ruft Browser auf, extrahiert Wetterdaten, trägt Werte ein, bewertet Temperatur, fügt Screenshots ein  
4. **Follow-Up** – Speichert Ergebnisdatei mit Zeitstempel, schließt Anwendungen  

### Ui.Vision RPA / Kantu
Der Ablauf ist in einem einzigen JSON-Makro abgebildet:
1. **Initialisierung** – Variablen setzen, Pfade definieren  
2. **Vorbereitung** – Excel-Dateien öffnen, Städte einfügen, Fenster anordnen  
3. **Hauptschleife** – Für jede Stadt: Wetterdaten via Google Widget extrahieren, Screenshots anfertigen, Daten eintragen, Temperatur interpretieren  
4. **Abschluss** – Ergebnisdatei mit Zeitstempel speichern, Anwendungen schließen  

---

## Hinweise zur Dateien

- **Power Automate Desktop**: Flows lassen sich mithilfe Strg + C als JSON exportieren. Hier werden sie in Einzeldateien pro Subflow abgelegt.  
- **Ui.Vision RPA / Kantu**: Makro liegt in einer einzigen JSON-Datei vor.  

---

## Nutzung

Dieses Repository dient der wissenschaftlichen Dokumentation.  
