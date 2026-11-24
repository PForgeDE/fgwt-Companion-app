# Installation und Updates

[← Dokumentation](README.md)

## Voraussetzungen

- Windows 10 oder 11, 64 Bit.
- **Microsoft Visual C++ 2015–2022 Redistributable (x64).** Die Standard-Erkennung PaddleOCR braucht es. Fehlt es, schlägt die Erkennung mit einem Fehler zu *ONNX Runtime* fehl. [Download bei Microsoft](https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist).
- Eine .NET-Installation ist **nicht** nötig; die App ist als eigenständige Windows-Anwendung gebaut.
- Optional für **Windows OCR**: ein OCR-Sprachpaket, siehe [FAQ](faq.md#windows-ocr-liest-nichts).

## Installieren

1. Auf der [Release-Seite](https://github.com/PForgeDE/fgwt-Companion-app/releases/latest) die Windows-Installationsdatei (`.msi`) herunterladen.
2. Die Datei starten und dem Installer folgen. Die MSI installiert die App für alle Benutzer des PCs; Windows fragt dafür nach Administratorrechten.
3. **FGWT Companion** aus dem Startmenü starten.

Beim ersten Start führt die Seite **Willkommen** durch drei Schritte: Spiel hinzufügen, mit FGWT verbinden, Module prüfen. Weiter geht es unter [Erste Schritte](erste-schritte.md).

## Updates

Die App prüft regelmäßig die Releases dieses Repositorys. Gibt es eine neue Version:

1. meldet sie sich mit einer Windows-Benachrichtigung,
2. zeigt unter **Einstellungen → Allgemein → Updates** die neue Version mit ihren Notizen,
3. lädt die Installationsdatei herunter und prüft ihre Prüfsumme (SHA-256),
4. installiert sie, sobald du auf **Installieren** klickst – auch während ein Spiel läuft.

Wann das Update passiert, entscheidest du. Intervall, Repository und ein optionaler Token stehen unter **Einstellungen → Allgemein → Updates**, wenn oben auf der Einstellungsseite **Erweiterte Einstellungen zeigen** an ist. Einen Token brauchst du nicht.

### Von einer Version vor 26.11.12

Versionen vor 26.11.12 suchen Updates in einem privaten Repository und brauchen dafür einen Token. Installiere **26.11.12 einmal von Hand** aus diesem Repository. Ab dann findet die App alle weiteren Updates hier, ohne Token. Deine Einstellungen und Daten bleiben dabei erhalten.

### Hinweis zu kommenden Versionen

Eine der nächsten Versionen stellt auf eine Installation **pro Benutzer** um: ein Setup (`FGWT-Companion-<Version>-win-x64-setup.exe`), das ohne Administratorrechte nach `%LocalAppData%\FgwtCompanion` installiert und künftig nur die geänderten Teile lädt. Wer bisher per MSI installiert hat, zieht beim nächsten selbst gestarteten Update um; die Daten in `%APPDATA%\FgwtCompanion` bleiben. Die alte Installation entfernst du danach unter **Einstellungen → Allgemein → Updates → Alte Installation entfernen…**; sie wird nie von selbst entfernt. Die Release-Notizen der betreffenden Version beschreiben den Umzug.

## Start mit Windows und Infobereich

Unter **Einstellungen → Allgemein → Start und Infobereich** gibt es drei Schalter, anfangs alle aus:

| Einstellung | Wirkung |
|---|---|
| Mit der Windows-Anmeldung starten | Startet die App bei deiner Anmeldung, nur für dein Windows-Konto. |
| Dann minimiert starten | Der Start mit Windows öffnet die App minimiert. Nur verfügbar, wenn die erste Einstellung an ist. |
| In den Infobereich statt in die Taskleiste minimieren | Minimiert verschwindet die App aus der Taskleiste und bleibt als Icon im Infobereich (Tray). Klick aufs Icon holt sie zurück; das Menü hat **Öffnen** und **Beenden**. |

Die App läuft nur einmal. Startest du sie erneut, holt das das laufende Fenster nach vorn, statt eine zweite Kopie zu öffnen.

Die App merkt sich Größe und Position ihres Fensters und öffnet beim nächsten Start die zuletzt benutzte Seite.

## Wo deine Daten liegen

Alles wird automatisch gespeichert, einen Speichern-Knopf gibt es nicht.

| Was | Wo |
|---|---|
| Einstellungen und Daten | `%APPDATA%\FgwtCompanion`, eine Datenbankdatei (`.db`) je Teil der App |
| Dateiorte im Detail | **Einstellungen → Spielwerte lesen** (mit *Erweiterte Einstellungen zeigen*) |
| Telemetrie-Aufnahmen | Ordner `telemetry` im Datenordner |
| Sicherungen vor Änderungen eines KI-Assistenten | Ordner `ai-backup` im Datenordner |

### Sichern und umziehen

- **Alles sichern oder auf einen anderen PC umziehen:** App schließen und den ganzen Datenordner kopieren.
- **Ein einzelnes Spiel weitergeben:** auf der Seite **Spiele** auf der Karte des Spiels **Teilen** und die Datei auf dem anderen PC mit **Spiel importieren…** öffnen. Siehe [Spiele teilen](spielwerte-lesen.md#spiele-teilen).

### Getrennte Profile

Startest du die App mit `--data` und einem anderen Ordner, ist das ein eigenes Profil mit eigenen Einstellungen. Es kann neben dem normalen Profil laufen. Am einfachsten legst du dafür eine Verknüpfung zur App an und hängst im Feld **Ziel** hinter den Programmpfad zum Beispiel `--data "D:\FGWT-Profil-Test"` an.

Für getrennte Einrichtungen für LIVE und PTU brauchst du kein eigenes Profil, siehe [FAQ](faq.md#wie-halte-ich-getrennte-setups-für-live-und-ptu).

## Deinstallieren

**Windows-Einstellungen → Apps → FGWT Companion → Deinstallieren.** Der Start mit Windows wird dabei entfernt. Deine Daten in `%APPDATA%\FgwtCompanion` bleiben; lösche den Ordner von Hand, wenn du auch sie entfernen willst.

## Linux

Ein Linux-Build ist in Arbeit, aber noch nicht Teil der Releases. Die Releases enthalten nur die Windows-Installation.
