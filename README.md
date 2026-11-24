<div align="center">

# FGWT Companion

**Spielwerte lesen, im Overlay zeigen – und für Star Citizen Handel, Fracht, Verträge und Spielabende mitschreiben.**

[Download](https://github.com/PForgeDE/fgwt-Companion-app/releases/latest) ·
[Dokumentation](docs/README.md) ·
[Erste Schritte](docs/erste-schritte.md) ·
[FAQ](docs/faq.md) ·
[FGWT](https://fgwt.pforge.de/)

</div>

---

FGWT Companion ist eine Desktop-App für Windows. Sie liest Informationen aus einem laufenden Spiel und zeigt sie in einem Overlay, das immer obenauf liegt und Klicks zum Spiel durchlässt. Sie liest drei Arten von Quellen:

- **Bildschirmbereiche**, die du selbst festlegst, per OCR oder Symbolvergleich,
- **Log-Dateien**, die ein Spiel schreibt,
- für **Star Citizen** zusätzlich den lokalen Telemetrie-Dienst des Spiels.

Für Star Citizen macht die App aus der `Game.log` außerdem ein Handelsbuch, eine Übersicht der Frachtaufträge, eine Vertrags- und Blueprint-Historie und ein Logbuch pro Spielabend. Wenn du willst, sendet sie diese Daten an die Web-API der Star-Citizen-Organisation [FGWT](https://fgwt.pforge.de/).

Die App ist für alle Mitglieder von FGWT gedacht. Bildschirmlesen, Overlay-Designer und Anti-AFK funktionieren mit jedem Spiel.

> *English:* FGWT Companion is a Windows desktop app that reads values from a running game (screen OCR, log files, Star Citizen's local telemetry) and shows them in a click-through overlay. The app ships in English and German; this documentation is in German.

## Inhalt

- [Funktionen](#funktionen)
- [Download und Installation](#download-und-installation)
- [Schnellstart](#schnellstart)
- [Systemvoraussetzungen](#systemvoraussetzungen)
- [Dokumentation](#dokumentation)
- [Was die App liest und sendet](#was-die-app-liest-und-sendet)
- [Hilfe und Kontakt](#hilfe-und-kontakt)
- [Über dieses Repository](#über-dieses-repository)
- [Copyright und Hinweise](#copyright-und-hinweise)

## Funktionen

Die App besteht aus neun Modulen. Jedes schaltest du unter **Einstellungen → Module** an oder aus; ein ausgeschaltetes Modul behält seine Daten.

| Modul | Für | Was es tut |
|---|---|---|
| **Spielwerte lesen** (Game readings) | jedes Spiel | Regionen auf dem Bildschirm per PaddleOCR oder Windows-OCR lesen, Symbole erkennen und zählen, Anker für bewegte HUDs, Log-Dateien und Log-Regeln, Nachschlagelisten, Alarme mit Piepton, Sprache oder WAV, Modi und Layouts mit automatischem Wechsel, Checklisten, Presets, JavaScript-Skripte für Sonderfälle. Die Seite *Werte* zeigt alle aktuellen Spielwerte mit ihrer Quelle. |
| **Overlay-Designer** | jedes Spiel | Eigene Tafeln im Overlay aus Texten, Balken und Blöcken anderer Module, mit Bedingungen, eigenem Platz je Layout und Vollbild-Editor. |
| **Anti-AFK** | jedes Spiel | Bewegt die Maus in einem Muster oder drückt Tasten, solange das Spiel vorne ist und du nichts tust. Aus, bis du es einschaltest und den Hinweis bestätigst. |
| **Handel** (Trading) | Star Citizen | Paart Warenkäufe und -verkäufe zu Geschäften mit Gewinn, pro Spielsitzung; Verlauf mit Gewinndiagramm, Märkte, Routen, Warennamen. |
| **Fracht** (Hauling) | Star Citizen | Gruppiert angenommene Frachtaufträge zu Stapeln, zeigt eine Liefertabelle Ware nach Ziel und plant die Fracht in Kisten für das Frachtraster deines Schiffs. |
| **Verträge** (Contracts) | Star Citizen | Merkt sich jeden Vertrag mit Ausgang und die erhaltenen Blueprints. |
| **Logbuch** (Logbook) | Star Citizen | Pro Spielabend: Shards, Ladezeiten, Schiffe, Verletzungen, Rechtsgebiete, Kontostände; die Seite *Spielsitzungen* als „Brücke“ mit Uhr und Flugschreiber. |
| **Org live** | Star Citizen | Zeigt im Overlay, welche Org-Mitglieder gerade spielen, wo und in welchem Schiff. |
| **Telemetrie** | Star Citizen | Liest 41 Werte aus dem lokalen Telemetrie-Dienst von Star Citizen: Gesundheit, Sauerstoff, Schiff, Geschwindigkeit, Treibstoff, Warnlampen, Kontostand und mehr. |

Dazu kommen:

- **Overlay**, das von Bildschirmaufnahmen und Streams ausgenommen ist.
- **Postausgang**: Alle Anfragen an FGWT und andere APIs werden dauerhaft gespeichert und wiederholt, bis sie durchgehen, auch nach einem Neustart.
- **Spiele teilen**: Regionen, Listen und Modi eines Spiels als `.fgwt-game.json` an Org-Mitglieder weitergeben.
- **KI-Assistenten**: Claude Desktop, Claude Code oder ein anderer MCP-Client kann deine Einrichtung lesen und, wenn du es erlaubst, ändern.
- **Updates** direkt aus der App.
- **Sprachen**: Deutsch und Englisch, zur Laufzeit umschaltbar.

## Download und Installation

1. Öffne die [neueste Version](https://github.com/PForgeDE/fgwt-Companion-app/releases/latest).
2. Lade den Windows-Installer (`.msi`) herunter und starte ihn.
3. Starte **FGWT Companion** aus dem Startmenü.

Danach meldet die App neue Versionen selbst und installiert sie, sobald du auf **Installieren** klickst. Einen Token brauchst du dafür seit Version 26.11.12 nicht mehr.

> **Updatest du von einer Version vor 26.11.12?** Ältere Versionen suchen Updates noch an einem anderen Ort. Installiere 26.11.12 einmal von Hand aus diesem Repository; danach laufen die Updates wieder automatisch.

Mehr dazu, auch zu Datenordner, Sicherung und Deinstallation: [Installation und Updates](docs/installation.md).

## Schnellstart

Deine erste Region in fünf Minuten:

1. Spiel starten. Unter **Spiele** prüfen, dass es aufgeführt ist, sonst **Spiel hinzufügen** und seine `.exe` wählen.
2. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd> öffnet den Regionseditor auf einem eingefrorenen Screenshot.
3. Ein Rechteck eng um den Text ziehen, den du lesen willst, und ihm einen Namen geben.
4. Editor schließen, die Region unter **Regionen** wählen: Oben steht, was gerade gelesen wird.
5. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd> zeigt das Overlay. Mit <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd> entsperren, verschieben, wieder sperren.
6. <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>B</kbd> zeigt die Regionen auf dem Bildschirm: grün = Text gefunden, cyan = leer, rot = Fehler.

Für Star Citizen: Das Spiel mit seiner `StarCitizen.exe` einrichten. Dann erscheinen Handel, Fracht, Logbuch und die anderen Star-Citizen-Module von selbst. Ausführlich: [Erste Schritte](docs/erste-schritte.md).

## Systemvoraussetzungen

| | |
|---|---|
| Betriebssystem | Windows 10 oder 11, 64 Bit |
| Laufzeit | [Microsoft Visual C++ 2015–2022 Redistributable (x64)](https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist) für die PaddleOCR-Erkennung. Eine .NET-Installation ist nicht nötig. |
| Optional | Ein Windows-OCR-Sprachpaket, wenn du Windows OCR statt PaddleOCR nutzen willst |
| Star Citizen | Für die Star-Citizen-Module; für Telemetrie eine Zeile in der `user.cfg`, die die App auf Wunsch einträgt |
| FGWT | Ein FGWT-Konto und -Token, wenn du Daten an FGWT senden oder Org live nutzen willst |

Ein Linux-Build ist in Arbeit, aber noch nicht Teil der Releases.

## Dokumentation

| Seite | Inhalt |
|---|---|
| [Übersicht](docs/README.md) | Alle Seiten der Dokumentation |
| [Installation und Updates](docs/installation.md) | Installieren, aktualisieren, Datenordner, Sicherung, Profile, Deinstallation |
| [Erste Schritte](docs/erste-schritte.md) | Aufbau der App, Einstellungen, die erste Region, das Overlay |
| [Spielwerte lesen](docs/spielwerte-lesen.md) | Regionen, saubere Ergebnisse, Symbole, Nachschlagelisten, Alarme, Modi und Layouts, Log-Dateien und Log-Regeln, Ausgaben, Spiele teilen |
| [Overlay und Overlay-Designer](docs/overlay.md) | Das Overlay, eigene Tafeln, Streams und Aufnahmen |
| [Star Citizen](docs/star-citizen.md) | Handel, Fracht, Verträge, Logbuch, Telemetrie, Org live, Spielwerte aus der `Game.log` |
| [FGWT und andere APIs](docs/fgwt-und-apis.md) | Verbindung zu FGWT, Spielereignisse, Heartbeat, Telemetrie, weitere Endpunkte, Postausgang |
| [Anti-AFK](docs/anti-afk.md) | Einrichten, Grenzen, Risiken |
| [KI-Assistenten](docs/ki-assistenten.md) | MCP-Client verbinden, Rechte, was er sieht |
| [Tastenkürzel](docs/tastenkuerzel.md) | Alle Standardtasten |
| [Datenschutz und Sicherheit](docs/datenschutz.md) | Was die App liest, schreibt und sendet |
| [FAQ und Fehlerbehebung](docs/faq.md) | Häufige Fragen und Probleme |

Die App hat außerdem eine eigene Seite **Hilfe** mit Tutorials und Fragen; sie ist immer auf dem Stand deiner Version.

## Was die App liest und sendet

- Die App **liest nur**: Pixel deines Bildschirms, Log-Dateien des Spiels und, bei Star Citizen mit eingeschalteter Telemetrie, den lokalen Telemetrie-Dienst des Spiels.
- Sie **greift nicht auf den Speicher des Spiels zu** und verändert keine Spieldateien. Die einzige Ausnahme ist eine Zeile in der `user.cfg` von Star Citizen, und nur, wenn du auf **In user.cfg eintragen** klickst und bestätigst.
- Sie **sendet keine Eingaben an das Spiel**, außer mit Anti-AFK, das aus ist, bis du es ausdrücklich einschaltest.
- An **FGWT oder eine andere API** geht nur, was du unter **Einstellungen → FGWT** und **Weitere APIs** einschaltest. Tokens werden für dein Windows-Konto verschlüsselt gespeichert.

Details: [Datenschutz und Sicherheit](docs/datenschutz.md).

## Hilfe und Kontakt

- **In der App:** die Seite **Hilfe** (Icon unten in der Seitenleiste).
- **Fehler melden, Vorschläge, Fragen:** über das [Kontaktformular auf pforge.de](https://pforge.de/contact) oder im [PForge-Discord](https://discord.gg/nFVu53XbjT).
- **FGWT-Mitglieder** erreichen das Team auch über die üblichen Kanäle der Org.

Hilfreich bei einer Fehlermeldung: die Version (**Einstellungen → Allgemein → Updates**), was du getan hast und, wenn es um das Lesen geht, ein Screenshot der Region.

## Über dieses Repository

Dieses Repository enthält die **öffentlichen Releases** und die **Dokumentation für Spieler**. Der Quellcode liegt in einem privaten Repository und ist nicht Teil dieses Repositorys.

Versionen heißen `JJ.MM.Patch`, zum Beispiel `26.11.12` für das zwölfte Update im November 2026. Was sich in jeder Version geändert hat, steht in den [Release-Notizen](https://github.com/PForgeDE/fgwt-Companion-app/releases).

## Copyright und Hinweise

**Copyright © 2026 PForge (Phoenix Forge). Alle Rechte vorbehalten.**

FGWT Companion ist ein privates, nicht kommerzielles Projekt von [PForge](https://pforge.de/) für die Star-Citizen-Organisation FGWT. Die Nutzungsbedingungen stehen in [LICENSE](LICENSE).

Konzept und Entwicklung: AbythX, gebaut mit Claude Code.

FGWT Companion ist ein inoffizielles Fan-Projekt und steht in keiner Verbindung zu Cloud Imperium Games. *Star Citizen®* ist eine eingetragene Marke der Cloud Imperium Rights LLC. Alle anderen Marken gehören ihren jeweiligen Inhabern.

Die App nutzt Open-Source-Bibliotheken, unter anderem Avalonia, PaddleOCR (über RapidOcrNet und ONNX Runtime), SQLite, Dapper, Jint und Serilog. Für sie gelten ihre eigenen Lizenzen.
