# Erste Schritte

[← Dokumentation](README.md)

## Aufbau der App

**Seitenleiste, oben**

- **Willkommen** – nur, solange noch kein Spiel eingerichtet ist.
- **Spiele** und die Karte des aktiven Spiels.
- Darunter ein Eintrag je eingeschaltetem Modul, mit seinen Seiten als Reiter.

**Seitenleiste, „Auf FGWT“**

Links zur FGWT-Website, je nach eingeschalteten Modulen: *Missionen und Baupläne*, *Handel*, *Org live*. Diese Übersichten gibt es nur auf der Website, nicht als eigene Seiten in der App.

**Seitenleiste, unten**

Eine Reihe Icons – Einstellungen, Postausgang, Hilfe und weitere –, jedes mit Tooltip.

**Hinweise** der App erscheinen über jeder Seite außer den Einstellungen.

## Einstellungen

Die Einstellungen sind in Gruppen geordnet:

| Gruppe | Inhalt |
|---|---|
| Allgemein | Sprache, Animationen, Start und Infobereich, Alte Logs, Updates |
| Overlay und Alarme | Aussehen und Verhalten des Overlays, gesprochene Alarme |
| Tastenkürzel | Alle Hotkeys, siehe [Tastenkürzel](tastenkuerzel.md) |
| FGWT | Verbindung, Spielereignisse, Live-Status (Heartbeat und Telemetrie), siehe [FGWT und andere APIs](fgwt-und-apis.md) |
| Module | Jedes Modul an- und ausschalten |
| Weitere APIs | Eigene Endpunkte, siehe [FGWT und andere APIs](fgwt-und-apis.md#weitere-apis) |
| je Modul | Eine eigene Gruppe pro Modul |

Selten Gebrauchtes erscheint erst, wenn du oben auf der Einstellungsseite **Erweiterte Einstellungen zeigen** einschaltest. Jede Modulseite mit eigener Einstellungsgruppe hat außerdem einen Knopf **Einstellungen** im Kopf.

### Module

Unter **Einstellungen → Module** schaltest du jeden Teil der App an oder aus. Ein ausgeschaltetes Modul zeigt nichts und tut nichts, behält aber seine Daten.

Ein neues Profil startet mit wenigen Modulen. *Spielwerte lesen*, *Overlay-Designer*, *Telemetrie*, *Org live* und *Anti-AFK* sind anfangs aus. *Org live* geht von selbst an, sobald du einen FGWT-Token speicherst. *Anti-AFK* bleibt aus, bis du es selbst einschaltest.

Die Star-Citizen-Module (Handel, Fracht, Verträge, Logbuch, Org live, Telemetrie) erscheinen nur, solange das aktive Spiel Star Citizen ist.

### Sprache

**Einstellungen → Allgemein → Sprache.** Deutsch oder Englisch; *System* folgt der Anzeigesprache von Windows. Die Sprache wechselt sofort, ohne Neustart. Namen, die du selbst vergeben hast, bleiben, wie sie sind.

## Ein Spiel einrichten

1. Seite **Spiele** öffnen.
2. **Spiel hinzufügen** und die `.exe` des Spiels wählen. Oder **Laufendes Spiel wählen** anklicken und binnen 5 Sekunden ins Spiel wechseln.
3. Für Star Citizen die `StarCitizen.exe` wählen oder beim Spiel **Star Citizen** anhaken. Erst dann erscheinen die Star-Citizen-Module.

Das Spiel, dessen Fenster vorne ist, wird automatisch aktiv. Solange weder eines deiner Spiele noch die App selbst vorne ist, pausiert das Lesen.

Auf der Karte eines Spiels kannst du es außerdem **duplizieren**, **teilen**, seine **Log-Quellen** bearbeiten und den **Log-Betrachter** öffnen.

## Deine erste Region in fünf Minuten

Ziel: einen Wert aus dem HUD lesen und im Overlay anzeigen.

1. Spiel starten. Auf der Seite **Spiele** prüfen, dass es aufgeführt und aktiv ist.
2. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd> drücken oder auf der Seite **Regionen** auf **Regionen auf dem Bildschirm bearbeiten** klicken. Der Editor öffnet sich auf einem eingefrorenen Screenshot deines Monitors.
3. Ein Rechteck **eng** um den Text ziehen, den du lesen willst, z. B. den Quantentreibstoff, und ihm einen Namen geben.
4. Editor schließen und die Region auf der Seite **Regionen** wählen. Das Live-Ergebnis oben zeigt, was gerade gelesen wird.
5. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd> zeigt das Overlay. Mit <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd> entsperren, an eine freie Stelle ziehen und mit <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd> wieder sperren, damit Klicks zum Spiel durchgehen.
6. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>B</kbd> zeigt die Regionen auf dem Bildschirm: **grün** = Text gefunden, **cyan** = leer, **rot** = Fehler.

Liest die Region Unsinn? Weiter mit [Saubere Ergebnisse bekommen](spielwerte-lesen.md#saubere-ergebnisse-bekommen).

## Nächste Schritte

- [Alarme und gesprochene Ansagen](spielwerte-lesen.md#alarme) einrichten.
- Mit [Modi](spielwerte-lesen.md#modi) nur die Regionen laufen lassen, die du gerade brauchst.
- Eigene Tafeln mit dem [Overlay-Designer](overlay.md#overlay-designer) bauen.
- Für Star Citizen: [Handel, Fracht und Logbuch](star-citizen.md) und die [Verbindung zu FGWT](fgwt-und-apis.md).
