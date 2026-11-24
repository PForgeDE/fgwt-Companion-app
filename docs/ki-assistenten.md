# KI-Assistenten

[← Dokumentation](README.md)

Du kannst Claude Desktop, Claude Code oder einen anderen **MCP-Client** mit der App verbinden. Der Assistent liest deine Einrichtung, richtet – wenn du es erlaubst – Regionen, Nachschlagelisten, Log-Quellen und Log-Regeln für dich ein und beantwortet Fragen zu deinem Spiel, etwa „Was war diese Woche meine beste Route?“.

## Verbinden

1. Oben auf der Einstellungsseite **Erweiterte Einstellungen zeigen** einschalten.
2. **Einstellungen → Allgemein → KI-Assistenten:** **Jetzt starten** klicken oder **Mit der App starten** wählen.
3. **Kopieren** und den Eintrag in die MCP-Konfiguration deines Clients einfügen (Claude Desktop: *Settings → Developer → Edit Config*). Den Client neu starten.
4. Den Assistenten fragen – oder im Client einen der Prompts der App wählen: *Set up a game*, *Mining: name the rock from its signature*, *Warn me about unknown players*.

## Rechte

| Schalter | Erlaubt |
|---|---|
| *(immer, solange die Schnittstelle läuft)* | Lesen deiner Spiele, Module, Einstellungen, Log-Quellen und der Einrichtung von *Spielwerte lesen* |
| **Meine Spieldaten teilen** | Zusätzlich deine Handelsdaten, Sitzungen, Aufträge, Verträge, Telemetrie, Log-Einträge und die aktuellen Spielwerte |
| **Änderungen erlauben** | Änderungen an deiner Einrichtung |

**Nie angeboten** werden: Tokens und Schlüssel, Senden an FGWT oder eine andere API, Updates und das Löschen eines Spiels. Zuordnungen für andere APIs darf ein Assistent anlegen, aber nur ausgeschaltet; er sendet nie zum Test und schaltet nie eine Zuordnung ein.

Die Schnittstelle ist **nur von diesem PC aus** und nur für dein Windows-Konto erreichbar. Beachte aber: Was der Assistent liest, geht an den Anbieter deines Assistenten.

## Sicherung und Rückgängig machen

- Vor der ersten Änderung eines Assistenten in einer Sitzung kopiert die App ihre Datenbanken in den Ordner `ai-backup` im Datenordner.
- **Änderungen durch Assistenten** listet jede Änderung.
- Zurück zum Stand davor: App schließen und die `.db`-Dateien eines Ordners in `ai-backup` über die im Datenordner kopieren.
