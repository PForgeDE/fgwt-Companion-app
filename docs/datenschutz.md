# Datenschutz und Sicherheit

[← Dokumentation](README.md)

## Was die App liest

| Quelle | Wann |
|---|---|
| **Pixel deines Bildschirms** | In den Regionen, die du anlegst – so, wie du den Bildschirm liest |
| **Log-Dateien des Spiels** | Die Log-Quellen deiner Spiele, bei Star Citizen die `Game.log` |
| **Telemetrie von Star Citizen** | Nur mit eingeschaltetem Modul Telemetrie und eingeschaltetem Telemetrie-Dienst des Spiels; das Spiel sendet sie an Programme auf deinem PC |

Die App **greift nicht auf den Speicher des Spiels zu** und verändert das Spiel nicht.

Das Lesen pausiert, solange weder eines deiner Spiele noch die App selbst im Vordergrund ist.

## Was die App schreibt

- Ihre eigenen Daten in `%APPDATA%\FgwtCompanion` (bzw. den mit `--data` gewählten Ordner).
- **Die einzige Datei des Spiels**, die sie je schreibt, ist die `user.cfg` von Star Citizen: eine Zeile für die Telemetrie, und nur, nachdem du auf **In user.cfg eintragen** geklickt und bestätigt hast.
- Den Start mit Windows, wenn du ihn einschaltest.

## Eingaben an das Spiel

Die App sendet **keine Eingaben** an das Spiel – außer mit [Anti-AFK](anti-afk.md). Das Modul ist aus, bis du es einschaltest und seinen Hinweis bestätigst; erst gestartet bewegt es die Maus oder drückt deine Tasten.

## Skripte

Skripte in Regionen und Log-Regeln **rechnen nur**. Sie können nicht auf Dateien, Netzwerk oder andere Programme zugreifen. Das gilt auch für Skripte in Spieldateien, die du von anderen importierst.

## Was die App sendet

| Ziel | Was | Wann |
|---|---|---|
| **FGWT** | Spielereignisse, Heartbeat, Telemetrie, Geschäfte, Spielsitzungen, Hull-C-Reviews | Nur, was du unter **Einstellungen → FGWT** und in den Modulen einschaltest; anfangs ist alles aus |
| **Weitere APIs** | Records nach deinen Zuordnungen | Nur eingeschaltete Endpunkte und Zuordnungen |
| **GitHub** | Abfrage der Releases dieses Repositorys | Für die Update-Prüfung |
| **star-citizen.wiki** | Nachschlagen von Warennamen | Im Modul Handel |
| **Anbieter deines KI-Assistenten** | Was der Assistent liest | Nur, wenn du einen Assistenten verbindest; siehe [KI-Assistenten](ki-assistenten.md) |

Welche Spielereignisse an FGWT gehen, kannst du bis auf jede einzelne Art steuern, siehe [Spielereignisse](fgwt-und-apis.md#spielereignisse). Was auf FGWT mit den Daten geschieht, regelt die Datenschutzerklärung der FGWT-Website.

Der **Log-Betrachter** und die Log-Einträge im Speicher werden nirgends hin gesendet. **Alte Logs**, die du einliest, gehen nicht an FGWT.

## Tokens und Schlüssel

- Tokens für FGWT und andere APIs werden **verschlüsselt für dein Windows-Konto** auf diesem PC gespeichert.
- Sie stehen **nie** in geteilten Spieldateien (`.fgwt-game.json`) und nie in exportierten Endpunkten.
- Ein KI-Assistent bekommt sie **nie** zu sehen.

## Streams und Aufnahmen

Overlay, Beschriftungen und Regionsrahmen werden aus Bildschirmaufnahmen herausgehalten. Zuschauer sehen das saubere Spiel, und die App liest nie ihr eigenes Overlay.

## Updates

Updates kommen aus den Releases dieses Repositorys. Die App prüft vor der Installation die SHA-256-Prüfsumme der heruntergeladenen Datei und installiert nur, wenn du **Installieren** wählst.
