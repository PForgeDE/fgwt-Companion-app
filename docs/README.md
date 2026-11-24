# FGWT Companion – Dokumentation

Diese Dokumentation beschreibt FGWT Companion ab Version **26.11.12**. Die Beschriftungen folgen der deutschen Oberfläche; wo die englische Bezeichnung beim Suchen hilft, steht sie in Klammern.

Maßgeblich ist immer die Seite **Hilfe** in der App: Sie gehört zu deiner Version. Weicht diese Dokumentation davon ab, hat die App recht.

## Für den Einstieg

| Seite | Inhalt |
|---|---|
| [Installation und Updates](installation.md) | Installieren, aktualisieren, Datenordner, Sicherung, Profile, Deinstallation |
| [Erste Schritte](erste-schritte.md) | Aufbau der App, Einstellungen, die erste Region, das Overlay |
| [Tastenkürzel](tastenkuerzel.md) | Alle Standardtasten auf einen Blick |
| [FAQ und Fehlerbehebung](faq.md) | Häufige Fragen und Probleme |

## Funktionen

| Seite | Inhalt |
|---|---|
| [Spielwerte lesen](spielwerte-lesen.md) | Regionen, OCR, Symbole, Nachschlagelisten, Alarme, Modi, Layouts, Log-Dateien, Log-Regeln, Ausgaben, Spiele teilen |
| [Overlay und Overlay-Designer](overlay.md) | Das Overlay, eigene Tafeln, Streams und Aufnahmen |
| [Star Citizen](star-citizen.md) | Handel, Fracht, Verträge, Logbuch, Telemetrie, Org live |
| [FGWT und andere APIs](fgwt-und-apis.md) | FGWT-Verbindung, Spielereignisse, Heartbeat, Telemetrie, weitere Endpunkte, Postausgang |
| [Anti-AFK](anti-afk.md) | Angemeldet bleiben, während du weg bist |
| [KI-Assistenten](ki-assistenten.md) | Claude oder einen anderen MCP-Client mit der App verbinden |

## Hintergrund

| Seite | Inhalt |
|---|---|
| [Datenschutz und Sicherheit](datenschutz.md) | Was die App liest, schreibt und sendet |

## Begriffe

| Begriff | Bedeutung |
|---|---|
| **Spiel** | Ein Eintrag auf der Seite *Spiele*. Jedes Spiel hat eigene Regionen, Modi, Layouts, Listen und Presets. Das Spiel, dessen Fenster vorne ist, ist das **aktive Spiel**. |
| **Region** | Ein Rechteck auf dem Bildschirm (oder eine Log-Datei), das die App regelmäßig liest. |
| **Spielwert** | Ein benannter Wert, den eine Region, eine Log-Regel, die Star-Citizen-Integration oder die Telemetrie liefert, z. B. `Cargo.people`, `starcitizen.ship`, `telemetry.speed`. Spielwerte lassen sich überall verwenden: in Ausgaben, Alarmen, Auslösern, Skripten und im Overlay-Designer. |
| **Ausgabe** | Was eine Region im Overlay zeigt: Text, Balken, Nachschlagen, Namensprüfung, Munition, Timer oder Geld. |
| **Modus** | Eine Tätigkeit wie Mining oder Kampf. Im aktiven Modus laufen nur seine Regionen. |
| **Layout** | Die Positionen der Regionen für ein bestimmtes HUD, etwa das einer Schiffsmarke. |
| **Log-Quelle** | Eine Log-Datei, die ein Spiel schreibt und die die App mitliest. |
| **Log-Regel** | Ein Muster, das aus passenden Log-Einträgen Spielwerte macht. |
| **Spielsitzung** | Ein Spielabend in Star Citizen; kann mehrere Spielstarts (auch nach Abstürzen) umfassen. |
| **Postausgang** (Outbox) | Die Warteschlange aller Anfragen an FGWT und andere APIs. |
