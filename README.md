# Rührwerks-Konfigurator

**Version 1.0.0 · Stand 21.11.2026 (MEZ) · für Volker Staffendt**

Browserbasierter Konfigurator für die **schematische Ersteinschätzung** und **Angebotsstruktur** von Rührtechnik an stehenden, runden Biogasbehältern (Fermenter, Nachgärer, Gärrestlager/Endlager, Vorgrube). Stil und Aufbau wie Doppelmembrangasspeicher- und Fermenter-Konfigurator.

> Technische Ersteinschätzung, keine verbindliche Hersteller-, Planungs- oder Preisauskunft. Auswahlregeln im Tool nach Festlegung Volker Staffendt, 21.11.2026. Finale Auslegung der Leistungen durch den Rührwerkshersteller.

## Start

`index.html` per Doppelklick im Browser öffnen. Eine Einzeldatei; three.js r158 ist eingebettet, keine Internetverbindung, keine Installation, kein Server. Projektstand und Preisliste bleiben nur lokal in diesem Browser (localStorage).

## Bedienung in Kürze

1. **Projekt:** Behälter anlegen, duplizieren, löschen. Testfälle aus der Arbeitsanweisung (Fall 1, Fall 1 mit 2 Paddeln, Fall 2, Fall 2 mit 2 TMR, Fall 3, Projekt 1 + 2) sind per Knopf ladbar.
2. **Fermenter-Import:** „Fermenter-JSON importieren“ übernimmt Typ, D, H, Wandstärke, Dach, max. Füllhöhe, Einbindung, Mittelstütze, TS-Angaben und die Substratmischung aus dem Projekt-JSON des Fermenter-Konfigurators. Die Kennzeichnung „hoher TS“ wird **nicht** automatisch gesetzt, sondern ist bewusst zu prüfen.
3. **Behälter:** Typ, Durchmesser, Höhe, Füllhöhe (leer = Annahme H − 0,5 m, sichtbar gekennzeichnet), Bezugsvolumen V = π/4 · D² · H_Füll (überschreibbar), Winkel des Substrateintrags.
4. **Substrat:** Gülle/NawaRo/Faserstoffe, Kennzeichnung „hoher TS / mist- oder feststoffreich“, TS-Werte nur zur Information.
5. **Rührwerke:** Bauart und Anzahl je Behälter. Der Vorschlag folgt den Festlegungen von Volker; Anzahl und Leistung (kW) bleiben Eingaben. Frequenzumrichter sind je Rührwerk vorgewählt und einzeln abwählbar.
6. **Elektro, Montage, Kran:** Kabelmeter, Steuerung (je Behälter / je Projekt / offen), Monteure, Montagetage, Inbetriebnahme, Kranstunden, Übernachtungen. Leere Felder bleiben „Menge offen“; eine eingetragene 0 bleibt 0.

## Festlegungen Volker Staffendt, 21.11.2026 (haben Vorrang vor Literatur)

| ID | Regel im Tool |
|---|---|
| RW-V1 | Füllstandsverhalten aus dem Behältertyp: Fermenter/Nachgärer dauerhaft hoch, Gärrestlager/Endlager kann bis 0 sinken. Vorgrube offen. Überschreiben nur mit Warnung. |
| RW-V2 | Endlager bzw. Füllstand bis 0: **keine Paddelrührwerke, keine hoch eingebauten Stabrührwerke.** Vorschlag Tauchmotorrührwerk höhenverstellbar am Mast. Übersteuern nur mit dauerhafter Warnung. |
| RW-V3 | Fermenter/Nachgärer mit hohem TS: **2–4 Paddelrührwerke plus 1 hoch eingebautes Stabrührwerk nahe Substrateintrag.** Anzahl der Paddel wird nicht automatisch gesetzt („Bereich 2–4, Anzahl festlegen“). |
| RW-V4 | Das Stabrührwerk wird am Winkel des Substrateintrags platziert; fehlt der Winkel, erscheint ein Hinweis. |
| RW-V5 | Frequenzumrichter standardmäßig je Rührwerk, einzeln abwählbar („abgewählt“, nie 0 €). |
| RW-V6 | Herstellerneutral: keine Hersteller-, Typ- oder Baureihennamen in Oberfläche, Stückliste, Angebot oder Katalog. |

Literaturregeln (FNR-Leitfaden u. a.) sind nachrangig und als solche gekennzeichnet. Das vollständige Regelwerk mit Begründungen, Quellen und Status liegt beim Entwickler (`regeln.md`) und ist im Tool unter „Regelwerk“ und „Quellen“ sichtbar.

## Offene Angaben

Alles, was nicht festgelegt ist, erscheint als Eingabefeld, „Angabe offen“ oder „Menge offen“ – es werden keine Werte erfunden. Offen sind insbesondere: Paddelzahl je Durchmesser, Nennleistungen, Rührkonzept ohne hohen TS, Füllhöhe, Montagesätze und -tage, Explosionsschutz, TS-Schwelle für „hoher TS“, Vorgrube, Meterwert für „hoch eingebaut“. Die Liste steht im Tool unter „Offene Angaben und Berechnungsgrundlagen“.

## Angebot

- **Keine Preise im Programm.** Alle Preisfelder starten leer. Preise werden im Tool eingetragen und nur lokal gespeichert; mit „Preisliste speichern (JSON)“ lässt sich eine eigene Preisliste-Datei sichern und später wieder laden. Das Projekt-JSON enthält keine Preise.
- Zentrale Preisliste je Artikel; Individualpreise je Behälter über „Indiv.“.
- Leeres Preisfeld = „auf Anfrage“; offene Menge = „Menge offen“ bzw. „nach Aufwand / offen“. Solche Positionen gehen nie mit 0 € in die Summe; die Summen tragen dann den Hinweis „Summe ohne offene Positionen“. Eine bewusst eingetragene 0 bleibt 0.
- Anzeigemodi: Einzelpreise je Position · Summe je Behälter · nur Projektsumme.
- Rabatt (auf die Behältersumme), Nebenkosten und MwSt. sind einzeln abschaltbar.
- Ausgabe: „Angebot drucken / PDF“ (A4 über den Druckdialog des Browsers) und „Angebot als CSV“ (UTF-8 mit BOM, Semikolon, Dezimalkomma – direkt in Excel lesbar).

## Weitere Ausgaben

Ergebnisübersicht, Stückliste je Behälter nach Gewerken (Rührwerke, Halterung/Mast/Durchführung, Elektro, Montage, Kran/Übernachtung, Wartungsteile), Gesamtstückliste, Stückliste als CSV, Projekt als JSON, Druckansicht A4, 3-D-Ansicht mit Schnitt und Layern (Behälter, Füllspiegel, Rührwerke, Masten/Wellen, Antriebe). Die 3-D-Darstellung ist schematisch; Winkel der übrigen Rührwerke sind eine Darstellungsannahme.

## Grenzen

Keine Leistungsauslegung, keine Strömungsberechnung, keine Statik, kein Ex-Schutz-Konzept, keine Herstellerauswahl. Orientierungswerte zur spezifischen Leistung werden nur angezeigt und mit eingegebenen Werten verglichen, nie automatisch übernommen.
