# Technische Prüfung des F450-Projektpakets

## Kurzurteil

Die Unterlagen enthalten eine gute technische Grundlage, aber der DOCX-Bericht bezeichnet sich selbst als **Vorentwurf**. Die bereitgestellten Fotos zeigen einen Flight Controller auf einem Rahmenaufbau sowie einen Mission-Planner-Bildschirm mit ArduCopter V4.5.7 und Quad-X-Auswahl. Der Projektverantwortliche hat zusätzlich bestätigt, dass Testflüge durchgeführt und sowohl Mission Planner als auch Betaflight im Projekt verwendet wurden. Fluglogs und quantitative Ergebnisse liegen im Paket jedoch nicht vor.

## 1. Widerspruch: Betaflight vs. ArduPilot

- Der CV-Text nennt Betaflight.
- Der Projektbericht nennt ArduCopter.
- Der Screenshot zeigt Mission Planner 1.3.80 und ArduCopter V4.5.7.
- Der Projektverantwortliche hat bestätigt, dass sowohl Betaflight als auch Mission Planner verwendet wurden.

**Korrektur:** Beide Programme dürfen im Projektverlauf genannt werden. Die belegte Pixhawk-6C-Konfiguration ist ArduCopter 4.5.7 mit Mission Planner. Die genaue Zuordnung von Betaflight zu einer weiteren Hardware oder separaten Projektphase sollte bei Gelegenheit ergänzt werden; nicht den Eindruck erwecken, Betaflight sei die Firmware des dokumentierten Pixhawk-6C-Setups.

Empfohlene CV-Formulierung:
„Konfiguration des Pixhawk-6C-Flight-Controllers mit ArduCopter und Mission Planner; Auswahl des Quad-X-Frame-Typs und Vorbereitung der Sensor-, RC- und Failsafe-Konfiguration.“

Nur tatsächlich abgeschlossene Kalibrierungen und Testflüge als durchgeführt aufführen.

## 2. Projektstatus klar kennzeichnen

Der DOCX-Bericht sagt ausdrücklich:
- „konzeptioneller Entwurf und geplante Integration“
- „detaillierter Vorentwurf“
- keine erfundenen Messergebnisse
- mehrere Komponenten- und Messwerte noch offen

Die Fotos belegen:
- einen Pixhawk-Controller auf einem Rahmen-/Center-Plate-Aufbau;
- eine Mission-Planner-Ansicht mit ArduCopter V4.5.7 und Quad X;
- ein Bild von Rahmenteilen, das wie ein Komponenten-/Referenzbild aussieht, nicht wie ein Foto des fertig montierten Copters.

Der Projektverantwortliche bestätigt zusätzlich, dass Testflüge durchgeführt wurden. Da keine Fluglogs oder Messprotokolle beigefügt sind, können Flugzeit, Reichweite, Stabilität oder konkrete Leistungswerte nicht unabhängig aus den Dateien verifiziert werden.

**Korrektur:** Testflüge dürfen als durchgeführt beschrieben werden. Konkrete Ergebnisse oder Leistungskennzahlen nur mit ergänzenden Logs/Messprotokollen angeben.

## 3. Komponenten – was die Dateien tatsächlich hergeben

- Motordatenblatt: HAWK'S WORK A2212, 920 KV; empfohlene Propeller 9450 oder 1045; Spannungsbereich 7.4–14.8 V, 2S–4S.
- ESC-Handbuch: Lumenier 30A BLHeli_S OPTO, 2–4S; 30 A konstant / 35 A Burst laut Handbuch; ausdrücklich ohne BEC.
- Bericht: Pixhawk 6C, vier 2212/920KV-Motoren, vier 30A-ESCs, 3S 5200mAh LiPo und 10x4.5-Propeller als Entwurfs-/Auswahlwerte.

**Offen:** Die PDF-Handbücher beweisen Modell-Spezifikationen, nicht, dass alle genannten Teile tatsächlich gekauft und verbaut wurden. 10x4.5 muss gegen das konkrete Motordatenblatt und Messwerte geprüft werden; das mitgelieferte Motordatenblatt empfiehlt 9450 oder 1045.

## 4. Elektrische Zeichnung korrigieren

Die mitgelieferte kleine Verdrahtungsskizze ist nicht ausreichend eindeutig für einen tatsächlichen Anschlussplan. Insbesondere ist die Position des Power Module im Hauptstrompfad nicht eindeutig dargestellt.

**Korrektur im neuen Paket:** Ein konzeptionelles Blockdiagramm zeigt Akku → Power Module → PDB → ESCs. Das ersetzt kein herstellerspezifisches Wiring Diagram. Vor Anschluss sind das exakte Power-Module-Modell, Pinout, Stromsensorbereich, FC-Port und Masseführung zu prüfen.

Da die ESCs laut Handbuch OPTO und ohne BEC sind, darf keine 5-V-Versorgung aus den ESCs angenommen werden. Die FC-Versorgung muss über das geeignete Pixhawk-kompatible Power Module gemäß dessen Handbuch erfolgen.

## 5. Berechnungen

Die im Bericht gezeigten Rechenschritte sind rechnerisch konsistent:
- 920 KV × 11.1 V = 10,212 rpm (idealisierte Leerlauf-Näherung).
- 11.1 V × 5.2 Ah = 57.72 Wh nominal.
- 80 % davon = 46.176 Wh als reine Planungsannahme.

Die daraus abgeleitete Flugzeit ist keine Messung. Keine konkrete Flugzeit, Schubleistung oder Stromreserve als erreicht veröffentlichen, solange Fluglogs/Prüfstandsmessungen und Herstellerkennlinien fehlen.

## 6. Weitere redaktionelle Korrekturen

- Studiengangsbezeichnung im DOCX sprachlich vereinheitlichen (z. B. „Elektro- und Informationstechnik“).
- Titel/Status so ändern, dass der Vorentwurfscharakter klar bleibt.
- Das DOCX-Datum 20. Juni 2026 von später aufgenommenen Fotos unterscheiden; Bilddaten nicht als damaligen Projektstand ausgeben.
- Externe Referenzfotos und vollständige Herstellerhandbücher nicht ohne Prüfung der Nutzungsrechte in ein öffentliches Repository kopieren.
- Die rechtlichen Angaben zu EASA/Drohnenbetrieb sind vor Veröffentlichung bzw. Flug anhand aktueller offizieller Quellen zu prüfen; der Bericht ist keine Flugfreigabe.

## Empfohlener Projektstatus für GitHub

„F450-Quad-X-Aufbau, Konfiguration und praktische Erprobung. Der Projektverantwortliche bestätigt durchgeführte Testflüge und die Verwendung von Mission Planner sowie Betaflight. Die bereitgestellten Unterlagen dokumentieren konkret die Pixhawk-6C-Konfiguration mit ArduCopter 4.5.7 und Quad X. Quantitative Flugergebnisse werden mangels beigefügter Logs/Messprotokolle nicht angegeben.“
