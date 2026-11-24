# FAQ und Fehlerbehebung

[← Dokumentation](README.md)

**Overlay und Bedienung**

- [Ich sehe das Overlay im Spiel nicht.](#ich-sehe-das-overlay-im-spiel-nicht)
- [Oben steht „Spiel nicht im Vordergrund“, obwohl ich spiele.](#oben-steht-spiel-nicht-im-vordergrund-obwohl-ich-spiele)
- [Warum fehlt das Overlay in meinem Stream oder meiner Aufnahme?](#warum-fehlt-das-overlay-in-meinem-stream-oder-meiner-aufnahme)
- [Ein Tastenkürzel tut nichts.](#ein-tastenkürzel-tut-nichts)

**Lesen und Erkennung**

- [Eine Region zeigt falsche Zeichen oder zufälligen Text.](#eine-region-zeigt-falsche-zeichen-oder-zufälligen-text)
- [Welche OCR-Engine soll ich nehmen?](#welche-ocr-engine-soll-ich-nehmen)
- [Windows OCR liest nichts.](#windows-ocr-liest-nichts)
- [Die Erkennung schlägt mit einem Fehler zu ONNX Runtime fehl.](#die-erkennung-schlägt-mit-einem-fehler-zu-onnx-runtime-fehl)
- [Die App braucht viel CPU.](#die-app-braucht-viel-cpu)
- [Meine Regionen sind an der falschen Stelle.](#meine-regionen-sind-an-der-falschen-stelle)
- [Wie setze ich Munitions-, Timer- oder Geldwerte zurück?](#wie-setze-ich-munitions--timer--oder-geldwerte-zurück)

**Star Citizen und FGWT**

- [Ich sehe Handel oder Fracht nicht in der Seitenleiste.](#ich-sehe-handel-oder-fracht-nicht-in-der-seitenleiste)
- [Wie halte ich getrennte Setups für LIVE und PTU?](#wie-halte-ich-getrennte-setups-für-live-und-ptu)
- [Die Seite Telemetrie zeigt nicht „Verbunden“.](#die-seite-telemetrie-zeigt-nicht-verbunden)
- [Warum zeigt eine Spielsitzung keinen Heartbeat und keinen Telemetrie-Frame?](#warum-zeigt-eine-spielsitzung-keinen-heartbeat-und-keinen-telemetrie-frame)
- [Org live zeigt niemanden.](#org-live-zeigt-niemanden)

**Daten und App**

- [Wo werden meine Einstellungen gespeichert?](#wo-werden-meine-einstellungen-gespeichert)
- [Wie sichere ich mein Setup oder ziehe es auf einen anderen PC um?](#wie-sichere-ich-mein-setup-oder-ziehe-es-auf-einen-anderen-pc-um)
- [Verändert oder liest die App das Spiel selbst?](#verändert-oder-liest-die-app-das-spiel-selbst)
- [Die App findet keine Updates.](#die-app-findet-keine-updates)
- [Wie ändere ich die Sprache?](#wie-ändere-ich-die-sprache)

---

## Ich sehe das Overlay im Spiel nicht.

Prüf, dass **Overlay** oben eingeschaltet ist, oder drück <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd>. Das Overlay verschwindet, solange das Spiel nicht im Vordergrund ist und solange das Scannen pausiert ist. Außerdem listet es nur Regionen des aktiven Modus, bei denen **Im Overlay anzeigen** an ist. Star Citizen im Vollbild ist kein Problem.

## Oben steht „Spiel nicht im Vordergrund“, obwohl ich spiele.

Die App erkennt das Spielfenster nicht. Bearbeite das Spiel auf der Seite **Spiele** und prüf seine Prozessnamen (Task-Manager → Details, ohne `.exe`) oder wähl seine ausführbare Datei mit **Durchsuchen…**. Das Scannen pausiert absichtlich, solange weder eines deiner Spiele noch die App vorne ist; das lässt sich unter **Einstellungen → Spielwerte lesen → Standards fürs Scannen** abschalten.

## Warum fehlt das Overlay in meinem Stream oder meiner Aufnahme?

Absichtlich: Overlay, Beschriftungen und Regionsrahmen werden aus Bildschirmaufnahmen herausgehalten, damit sie nie in dem landen, was die App liest – und deine Zuschauer das saubere Spiel sehen.

## Ein Tastenkürzel tut nichts.

Vielleicht nutzt ein anderes Programm es schon. Unter **Einstellungen → Tastenkürzel** sind Tasten markiert, die belegt sind, doppelt vorkommen oder auf vielen Tastaturen AltGr-Zeichen sind (<kbd>Strg</kbd>+<kbd>Alt</kbd>+…). Klick auf eine Taste und drück eine neue Kombination. Siehe [Tastenkürzel](tastenkuerzel.md).

## Eine Region zeigt falsche Zeichen oder zufälligen Text.

Folge [Saubere Ergebnisse bekommen](spielwerte-lesen.md#saubere-ergebnisse-bekommen). Am schnellsten hilft: Region eng um den Text halten, für Zahlen erlaubte Zeichen eintragen, kleine Schrift vergrößern und die **Min. Konfidenz** erhöhen, wenn leere Regionen Störungen zeigen.

## Welche OCR-Engine soll ich nehmen?

**PaddleOCR** (Standard) liest HUD-Schriften am besten und liefert nichts für Regionen ohne Text. **Windows OCR** ist viel schneller, aber ungenauer und hat keine Konfidenz. Den Standard stellst du unter **Einstellungen → Spielwerte lesen** ein und überschreibst ihn pro Region im Reiter *Erkennung*.

## Windows OCR liest nichts.

Windows OCR braucht ein installiertes OCR-Sprachpaket. Englisch installierst du in PowerShell **als Administrator**:

```powershell
Add-WindowsCapability -Online -Name "Language.OCR~~~en-US~0.0.1.0"
```

## Die Erkennung schlägt mit einem Fehler zu ONNX Runtime fehl.

PaddleOCR braucht das **Microsoft Visual C++ 2015–2022 Redistributable (x64)**. Installier es von [Microsoft](https://learn.microsoft.com/cpp/windows/latest-supported-vc-redist) und starte die App neu.

## Die App braucht viel CPU.

Jede Region kostet bei jedem Scan OCR-Zeit.

- Nutze [Modi](spielwerte-lesen.md#modi), damit nur die nötigen Regionen laufen.
- Gib selten wechselnden Regionen im Reiter *Scannen* ein längeres Intervall.
- Nutze **Nur solange diese Region Text zeigt**, damit z. B. Mining-Regionen nur bei offenem Scanner laufen.
- Windows OCR ist bei großem, klarem Text günstiger als PaddleOCR.
- Für Star Citizen liefert die [Telemetrie](star-citizen.md#telemetrie) viele Werte ganz ohne OCR.

## Meine Regionen sind an der falschen Stelle.

Positionen sind Bildschirmpixel. Nach einer Änderung von Auflösung, HUD-Größe oder Monitor verschieb sie im Regionseditor (<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd>) – prüf unter Einstellungen, dass er auf dem richtigen Monitor öffnet. Liegen nur manche Schiffe daneben, haben sie ein anderes HUD: Leg ein [Layout](spielwerte-lesen.md#layouts) für sie an.

## Wie setze ich Munitions-, Timer- oder Geldwerte zurück?

Klick unter den Ausgaben der Region auf **Letzte Werte vergessen**, z. B. nach einem Waffenwechsel, nach dem Abholen eines Raffinerieauftrags oder für eine neue Geld-Sitzung. Diese Werte gibt es nur, solange die App läuft.

## Ich sehe Handel oder Fracht nicht in der Seitenleiste.

Sie erscheinen nur, solange das aktive Spiel Star Citizen ist: Bearbeite das Spiel auf der Seite **Spiele** und wähl mit **Durchsuchen…** seine `StarCitizen.exe` (oder hake **Star Citizen** an). Außerdem müssen sie unter **Einstellungen → Module** an sein.

## Wie halte ich getrennte Setups für LIVE und PTU?

Mach daraus zwei Spiele: **Duplizieren** auf der Star-Citizen-Karte erstellt eine Kopie mit allem; dann die Kopie bearbeiten und die `StarCitizen.exe` des PTU wählen. Ein Spiel mit ausführbarer Datei hat Vorrang vor einem, das nur den Prozess nennt.

## Die Seite Telemetrie zeigt nicht „Verbunden“.

- Steht die Zeile aus **Einstellungen → Telemetrie** in der `user.cfg` des Spiels, das du startest (LIVE oder PTU)?
- Hast du das Spiel **nach** dem Eintragen neu gestartet? Es liest die `user.cfg` nur beim Start.
- Bist du schon **im Universum**? Im Menü sendet das Spiel nichts.
- Ist das Modul **Telemetrie** unter **Einstellungen → Module** an?

## Warum zeigt eine Spielsitzung keinen Heartbeat und keinen Telemetrie-Frame?

Für jeden Spiellauf behält die App nur den letzten Heartbeat und den letzten Telemetrie-Frame, die an FGWT gingen – den Frame höchstens alle 10 Sekunden. Sitzungen, in denen nichts an FGWT ging (Senden unter **Einstellungen → FGWT** aus, Modul Telemetrie aus, kein FGWT-Token), und Sitzungen aus älteren Versionen haben keinen.

## Org live zeigt niemanden.

- Hat dein FGWT-Token den Scope `live:read`? **Einstellungen → FGWT → Test** zeigt es. Ältere Tokens haben ihn nicht – auf der Website einen neuen erstellen.
- Es erscheinen nur Mitglieder, die auf der Website das Teilen ihres Live-Status eingeschaltet haben und gerade spielen.
- Das Overlay-Widget musst du unter **Einstellungen → Org live** selbst einschalten.

Siehe [Org live](star-citizen.md#org-live).

## Wo werden meine Einstellungen gespeichert?

Alles wird automatisch in `%APPDATA%\FgwtCompanion` gespeichert, eine Datenbankdatei je Teil der App – einen Speichern-Knopf gibt es nicht. Für ein getrenntes Profil starte die App mit `--data` und einem anderen Ordner. Siehe [Installation](installation.md#wo-deine-daten-liegen).

## Wie sichere ich mein Setup oder ziehe es auf einen anderen PC um?

Schließ die App und kopier den Datenordner – das ist alles. Oder nutze **Teilen** auf einer Spielkarte für ein einzelnes Spiel und **Spiel importieren…** auf dem anderen PC.

## Verändert oder liest die App das Spiel selbst?

Nein. Sie schaut nur auf Pixel deines Bildschirms, auf Log-Dateien, die das Spiel schreibt, und – mit eingeschaltetem Modul Telemetrie – auf das, was Star Citizen Programmen auf diesem PC sagt. Sie greift nicht auf den Speicher des Spiels zu und schickt keine Eingaben an das Spiel, außer mit [Anti-AFK](anti-afk.md). Die einzige Datei des Spiels, die sie je schreibt, ist eine Zeile in der `user.cfg` von Star Citizen, nachdem du zugestimmt hast. Mehr: [Datenschutz und Sicherheit](datenschutz.md).

## Die App findet keine Updates.

Versionen vor 26.11.12 suchen Updates noch an einem alten Ort. Installiere 26.11.12 einmal von Hand von der [Release-Seite](https://github.com/PForgeDE/fgwt-Companion-app/releases); danach funktioniert die Update-Prüfung ohne Token. Siehe [Installation und Updates](installation.md#updates).

## Wie ändere ich die Sprache?

**Einstellungen → Allgemein → Sprache.** *System* folgt der Anzeigesprache von Windows. Namen, die du vergeben hast – Regionen, Modi, Listen –, bleiben, wie sie sind.
