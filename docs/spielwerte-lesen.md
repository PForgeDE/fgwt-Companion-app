# Spielwerte lesen

[← Dokumentation](README.md)

Das Modul **Spielwerte lesen** (Game readings) liest Werte aus jedem Spiel: vom Bildschirm per OCR oder Symbolvergleich und aus den Log-Dateien des Spiels. Es hat die Seiten **Regionen**, **Modi & Layouts**, **Nachschlagelisten**, **Log-Regeln** und **Werte**.

- [Regionen](#regionen)
- [Saubere Ergebnisse bekommen](#saubere-ergebnisse-bekommen)
- [OCR-Engine wählen](#ocr-engine-wählen)
- [Symbole statt Text erkennen](#symbole-statt-text-erkennen)
- [Ausgaben](#ausgaben)
- [Nachschlagelisten](#nachschlagelisten)
- [Alarme](#alarme)
- [Modi](#modi)
- [Layouts](#layouts)
- [Log-Dateien lesen](#log-dateien-lesen)
- [Log-Regeln](#log-regeln)
- [Alle Spielwerte auf einen Blick](#alle-spielwerte-auf-einen-blick)
- [Skripte](#skripte)
- [Spiele teilen](#spiele-teilen)

## Regionen

Eine Region ist ein Rechteck auf dem Bildschirm, das die App regelmäßig liest. Du legst Regionen im **Regionseditor** an (<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>E</kbd>), der auf einem eingefrorenen Screenshot öffnet. Die Anleitung für die erste Region steht unter [Erste Schritte](erste-schritte.md#deine-erste-region-in-fünf-minuten).

Jede Region hat Reiter für **Erkennung**, **Textnachbearbeitung**, **Ausgabe**, **Scannen** und **Alarme**.

- **Namen** von Regionen enthalten keinen Punkt, weil sie Spielwerte benennen: Eine Region `Cargo` liefert `Cargo.text`, `Cargo.1` für die erste Zahl und `Cargo.people` für eine benannte Gruppe *people*. Zwei Regionen oder Log-Regeln eines Spiels dürfen nicht denselben Namen haben.
- **Tags:** Im Kopf einer Region eigene Tags vergeben, z. B. „HUD“, „mobiGlas“, „Schiff“. Die Chips über der Regionsliste filtern dann danach. Tags reisen mit, wenn eine Region kopiert oder geteilt wird.
- **Anker** lassen eine Region einem HUD folgen, das sich bewegt.
- **Presets:** Unter *Erkennung* mit **Als neues Preset speichern** die Einstellungen einer gut lesenden Region speichern und für ähnliche Regionen nutzen; sie bleiben synchron.
- **Nur solange diese Region Text zeigt:** Eine Region läuft nur, solange eine andere etwas zeigt – etwa Mining-Regionen nur bei offenem Scanner.
- **Positionen** sind Bildschirmpixel. Nach einem Wechsel von Auflösung, HUD-Größe oder Monitor die Regionen im Editor nachziehen.

## Saubere Ergebnisse bekommen

Was tun, wenn eine Region falsche Zeichen, Unsinn oder nichts liest:

1. Region auf der Seite **Regionen** wählen und ansehen, was die OCR sieht. Ziel: dunkler, scharfer Text auf hellem Grund.
2. Region **eng** um den Text halten. Jedes zusätzliche Stück HUD ist eine Chance für Störungen.
3. Kleine HUD-Schrift: **Vergrößern** auf 2–4×. Unruhiger Hintergrund: **Schwarz/Weiß (Otsu)** probieren oder im Regionseditor mit **Vom Bildschirm aufnehmen** die Textfarbe wählen.
4. Für Zahlen die **erlaubten Zeichen** eintragen, z. B. `0123456789.,%`. Das allein behebt die meisten Lesefehler.
5. Leere Regionen zeigen Unsinn? **Min. Konfidenz** erhöhen. Echter Text verschwindet? Senken.
6. Flackernde Werte oder Fehlalarme: unter *Textnachbearbeitung → Erweitert* **Lesungen bestätigen** als letzten Schritt hinzufügen.
7. Zufrieden? Als Preset speichern (siehe oben).

Bild- und Textschritte lassen sich zu Ketten kombinieren; mit Beispielaufnahmen kannst du sie ohne laufendes Spiel testen.

## OCR-Engine wählen

| Engine | Stärken | Schwächen |
|---|---|---|
| **PaddleOCR** (Standard) | Liest HUD-Schriften am besten; liefert nichts für Regionen ohne Text | Braucht mehr CPU; braucht die Visual-C++-Laufzeit |
| **Windows OCR** | Viel schneller | Ungenauer, keine Konfidenz, kann Störungen also nicht filtern; braucht ein OCR-Sprachpaket |

Den Standard stellst du unter **Einstellungen → Spielwerte lesen** ein und überschreibst ihn pro Region im Reiter *Erkennung* – z. B. Windows OCR für eine große, klare Zahl, die oft gescannt wird.

## Symbole statt Text erkennen

Fahrwerk ausgefahren, Quantum bereit, verbleibende Raketen – alles, was das HUD als Symbol zeigt.

1. Im Regionseditor eine Region eng um das Symbol zeichnen und **Als Symbolvorlage speichern**.
2. Die Vorlage nach ihrer Bedeutung benennen, z. B. „Fahrwerk unten“. Weitere Vorlagen für andere Symbole oder Zustände anlegen.
3. Im Reiter *Erkennung* **Erkennen** auf **Bild** stellen. Die Region größer machen, wenn sich das Symbol bewegen kann – es wird überall darin gefunden. Gleiche Symbole lassen sich auch zählen.
4. Die Region zeigt jetzt den Namen des gefundenen Symbols und lässt sich wie Text nutzen: für einen *Enthält*-Alarm, einen Modus-Auslöser oder *Nur solange diese Region Text zeigt*.
5. Wird es nicht zuverlässig gefunden? **Min. Ähnlichkeit** anpassen. *Was die Erkennung sieht* listet jede Vorlage mit ihrer Ähnlichkeit. Vorlagen in der Auflösung und HUD-Größe aufnehmen, mit der du spielst.

## Ausgaben

Was eine Region im Overlay zeigt, wählst du im Reiter **Ausgabe**. Mehrere Ausgaben pro Region sind möglich. **Wo** legt fest, ob das Ergebnis in der Overlay-Liste oder **neben der Region** steht.

| Ausgabe | Was sie zeigt |
|---|---|
| **Text** | Eine Zeile aus einer Vorlage, siehe unten |
| **Balken** | Ein Wert gegen seinen vollen Wert, gelb und rot ab Schwellen – fürs Knappwerden (Munition, Treibstoff) oder Vollwerden (Hitze) |
| **Nachschlagen** | Liest eine Zahl und zeigt die passenden Einträge einer [Nachschlageliste](#nachschlagelisten) |
| **Namensprüfung** | Ein Name pro Zeile gegen eine Liste erlaubter oder gesperrter Namen; andere sind eine Warnung |
| **Munition** | Zähler wie „30 / 240“; behält den letzten Wert ungleich null, wenn das HUD ihn kurz verliert |
| **Timer** | Ein Countdown wie „02:15:30“, der weiterzählt, wenn er nicht mehr sichtbar ist; zeigt `✓ done <Zeit>` und löst beim Ablauf einen Alarm aus |
| **Geld** | Ein Kontostand mit Tausenderkommas (36,820,874): erste Lesung = Start der Sitzung, dann Start, aktueller Stand und Differenz |

### Textvorlagen

| Platzhalter | Bedeutung |
|---|---|
| `{text}` | Der Text nach den Formatschritten |
| `{1}`, `{people}` | Eine Zahl bzw. eine benannte Gruppe der Region |
| `{= people / capacity * 100 :0}` | Eine Rechnung, hier mit 0 Nachkommastellen |
| `{Cargo.people}`, `{Location.zone}`, `{starcitizen.ship}`, `{telemetry.speed}` | Ein Spielwert einer anderen Region, einer Log-Regel, der Star-Citizen-Integration oder der Telemetrie |
| `{= [Cargo hold].people / Cargo.capacity * 100 :0}` | Namen mit Leerzeichen stehen in Rechnungen in eckigen Klammern |

Fehlt ein Wert, wird die Zeile ausgeblendet. Eine Region, die 5 Sekunden lang nichts zeigt, verlässt die Overlay-Liste und kommt zurück, sobald sie wieder etwas zeigt.

**Letzte Werte vergessen** im Reiter *Ausgabe* setzt Munition, Timer und Geld zurück, z. B. nach einem Waffenwechsel oder für eine neue Geld-Sitzung. Diese Werte gibt es nur, solange die App läuft.

### Beispiel: Verdienst der Sitzung

1. mobiGlas-Startbildschirm oder einen Kiosk öffnen, damit der Kontostand sichtbar ist, und eine Region darüber zeichnen.
2. Im Reiter *Ausgabe* die Ausgabe **Geld** hinzufügen und **Text** entfernen.
3. Das Lesen absichern: erlaubte Zeichen `0123456789,.` und *Lesungen bestätigen*.
4. Als Erinnerung einen *Fehlt*-Alarm mit 0 s und der Nachricht „mobiGlas öffnen“ hinzufügen; er meldet sich, bis der erste Kontostand gelesen wurde.

Mit dem Modul [Telemetrie](star-citizen.md#telemetrie) kommt der Kontostand in Star Citizen auch ohne Bildschirmlesen.

## Nachschlagelisten

Eine Nachschlageliste übersetzt einen gelesenen Wert in etwas Lesbares.

**Beispiel Mining – Gesteinsart aus der Scan-Signatur:**

1. Auf der Seite **Nachschlagelisten** **Liste hinzufügen** und pro Gestein einen Eintrag anlegen: Name = Gesteinsart, Wert = Signatur. Alternativ eine CSV (`Name;Wert;Notiz`) importieren oder Zeilen aus einer Tabelle einfügen.
2. Eine **Toleranz** für OCR- und Rundungsunterschiede einstellen und **Vielfache erkennen** einschalten, damit 3800 als „Gestein B ×2“ erkannt wird.
3. Die Liste mit **Wert ausprobieren** prüfen – ganz ohne Spiel.
4. Im Regionseditor eine Region über die Signaturzahl zeichnen.
5. Im Reiter *Ausgabe* **Nachschlagen** hinzufügen (und *Text* entfernen) und die Liste wählen.
6. **Wo** auf **Neben der Region** stellen und das Label im Editor so ziehen, dass es das HUD nicht verdeckt.

Listen der Art **Erlaubte Namen** dienen außerdem der Namensprüfung und als Auslöser für [Layouts](#layouts).

## Alarme

Lass dich warnen – oder ansagen –, wenn der Treibstoff knapp wird, ein seltenes Erz auftaucht oder ein Status verschwindet.

1. Region wählen und **Alarm hinzufügen**.
2. Bedingung wählen: **Unter / Über** einer Zahl, **Enthält** einen Text, **Passt zu einem Muster**, **Geändert** oder **Fehlt** (ein Status, der immer sichtbar sein sollte).
3. Optional eine **Nachricht** wie „Tanken!“ eingeben – sie wird statt des Grunds angezeigt oder gesprochen.
4. Ton wählen: **Piepton**, **Sprechen** (Windows liest die Nachricht vor) oder **Datei** (eigene WAV).
5. Stimme, Lautstärke und Tempo: **Einstellungen → Overlay und Alarme → Gesprochene Alarme**; *Test* spielt ein Beispiel.
6. Eine alarmierende Region blinkt im Overlay rot. Einen Alarm, den du gerade nicht brauchst, besser ausschalten als löschen.

**Alarm auf einen anderen Spielwert:** Unter *Spielwert* einen Namen eingeben, z. B. `starcitizen.jurisdiction` oder `Cargo.people` – das Feld schlägt die vorhandenen Namen vor. Der Alarm prüft dann diesen Wert, lässt aber trotzdem diese Region blinken, und reagiert sofort, wenn sich der Wert ändert.

## Modi

Mining, Fracht, Kampf – jeder Modus scannt und zeigt nur seine eigenen Regionen. Das spart CPU und hält das Overlay aufgeräumt.

1. Auf der Seite **Modi & Layouts** pro Tätigkeit einen Modus anlegen.
2. Im Raster anhaken, zu welchen Modi jede Region gehört, oder **Immer**. Regionen ohne Modus laufen immer.
3. Modi wechseln über den Chip oben oder mit <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F1</kbd>…<kbd>F9</kbd> (in Listenreihenfolge).
4. **Automatisch wechseln:** einem Modus Auslöser geben – z. B. Region *Schiff* enthält „Prospector“ oder Spielwert `starcitizen.ship` enthält „Prospector“ – und **Auto** im Modus-Panel einschalten oder <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>F10</kbd> drücken. Ein Auslöser auf einen Spielwert schaltet sofort, auch wenn gerade keine Region gelesen wird.
5. **Checklisten:** Einem Modus eine Checkliste geben (ein Schritt pro Zeile). Sie erscheint im Overlay, solange der Modus aktiv ist; <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>N</kbd> hakt den nächsten Schritt ab.

Der aktive Modus ist selbst ein Spielwert: `screenreading.mode`.

## Layouts

Drake, Aegis, MISC … haben Treibstoff und Schilde an verschiedenen Stellen. Ein Layout merkt sich, wo.

1. Auf der Seite **Modi & Layouts** auf **+** neben *Layouts* klicken, nach dem HUD-Stil benennen (z. B. „Drake“) und aktivieren.
2. Im Regionseditor die Regionen verschieben, die in diesem HUD woanders liegen. Solange ein Layout aktiv ist, werden Positionen nur für dieses Layout gespeichert.
3. Nicht verschobene Regionen behalten ihre Standardposition. **Standard** im Modus-Panel kehrt zu den Standardpositionen zurück.
4. Layouts wechseln im Modus-Panel oder mit <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>F1</kbd>…<kbd>F9</kbd>.
5. **Automatisch wechseln:** pro Hersteller eine Nachschlageliste der Art *Erlaubte Namen* anlegen („Drake-Schiffe“: Cutlass, Corsair, …) und dem Layout einen Auslöser **In Liste** auf die Schiffsnamen-Region geben.

Das aktive Layout ist der Spielwert `screenreading.layout`.

## Log-Dateien lesen

Viele Spiele schreiben Ereignisse – Kills, Tode, Aufträge – in Log-Dateien. Die App kann sie mitlesen, ohne den Bildschirm zu lesen.

### Log-Quellen

Zuerst der App sagen, welche Log-Dateien ein Spiel schreibt: auf der Seite **Spiele** auf der Karte des Spiels **Log-Quellen** öffnen und pro Datei eine Quelle hinzufügen.

- **Pfad:** `%LOCALAPPDATA%` und andere Umgebungsvariablen funktionieren; `*` und `?` im Dateinamen wählen die neueste Datei.
- Optional: wohin das Spiel das Log der vorigen Sitzung verschiebt, und die Kodierung.
- **Test** zeigt, welche Datei der Pfad findet, und ihre ersten Zeilen.
- **Beim Start wiederholen:** Die App liest beim Start die vorige und die aktuelle Datei von vorn; sonst nur, was ab dann geschrieben wird.
- **Einträge:** wie Zeilen zu Einträgen werden – automatisch erkannt (Standard), eine Zeile je Eintrag oder eigene Regeln mit regulären Ausdrücken für Beginn, Fortsetzung und Ende. So bleibt z. B. ein Stacktrace bei der Zeile, zu der er gehört.

Ein Star-Citizen-Spiel hat seine `Game.log` schon als Quelle; ändere dort nur den Pfad, falls das Spiel sie an einem ungewöhnlichen Ort schreibt. Log-Quellen reisen mit einer geteilten Spieldatei – nach einem Import die Pfade prüfen.

### Log-Region

1. Eine Region hinzufügen und im Reiter *Erkennung* **Erkennen** auf **Logdatei** stellen.
2. Die Log-Quelle wählen.
3. Unter **Nur passende Einträge** ein Muster eingeben, z. B. `Actor Death` für Kills – leer heißt jeder Eintrag.
4. Einstellen, wie viele der neuesten Einträge gezeigt werden und wie viele Sekunden einer bleibt.
5. Die Einträge mit einem Textschritt **Ersetzen** kürzen und Alarme oder Sprache hinzufügen wie bei jeder Region.

### Log-Betrachter

Auf der Karte des Spiels **Log-Betrachter** (das Auge) öffnet ein eigenes Fenster, das neben App und Spiel offen bleibt:

- neue Einträge kommen herein, wie das Spiel sie schreibt; beim Start wiederholte sind als *replay* markiert,
- Filter mit Text oder regulärem Ausdruck, **Pause**/**Fortsetzen**, **Kopieren**,
- jeder Eintrag zeigt, welche [Log-Regeln](#log-regeln) ihn treffen und was sie darin finden; *Nur Einträge ohne Regel* zeigt, was noch nicht gelesen wird,
- **Regel erstellen** (auch per Rechtsklick) legt aus dem gewählten Eintrag eine Log-Regel an,
- für die `Game.log` von Star Citizen zeigt das Panel *Star Citizen liest*, was die App von selbst daraus liest.

Die App hält die neuesten 500 Einträge pro Quelle nur im Speicher; nichts davon wird gespeichert oder gesendet.

## Log-Regeln

Eine Log-Regel liest eine Log-Quelle im Hintergrund und macht aus passenden Einträgen **Spielwerte**, z. B. die Zone, in der du bist.

1. **Spielwerte lesen → Log-Regeln** öffnen und **Regel hinzufügen** – oder im Log-Betrachter einen Eintrag wählen und **Regel erstellen**.
2. Die Regel nach dem benennen, was sie liest, z. B. `Location`. Der Name ist der erste Teil ihrer Spielwerte und enthält daher keinen Punkt.
3. Quelle wählen und das **Muster** schreiben: ein regulärer Ausdruck, Groß- und Kleinschreibung egal. Benannte Gruppen werden zu Feldern: `Entered zone (?<zone>\w+)` ergibt das Feld *zone*. Für das, was ein Muster nicht ausdrücken kann, die Art auf **Skript** stellen.
4. Unter *Erzeugt* **Spielwerte** anhaken. Jedes Feld wird zu `Location.zone`, der ganze Treffer zu `Location.text`. **Werte behalten für** lässt einen Wert nach einigen Sekunden veralten; 0 behält ihn bis zum nächsten Treffer.
5. **Log-Ereignisse** anhaken, um die letzten 50 Treffer für Skripte zu behalten.
6. **Test** führt die Regel auf den neuesten Einträgen aus und zeigt, was sie treffen und welche Werte sie liefern würde. Dann **Speichern**.
7. Den Wert in jeder Textausgabe nutzen: `Du bist in {Location.zone}`.

Regeln laufen, sobald *Spielwerte lesen* an ist – in jedem Modus, egal ob das Spiel vorne ist. Eine Regel kann außerdem **API-Records** erzeugen, siehe [FGWT und andere APIs](fgwt-und-apis.md#eigene-records-aus-regeln-und-regionen).

## Alle Spielwerte auf einen Blick

Die Seite **Werte** zeigt jeden Spielwert, den das aktive Spiel gerade hat – aus allen Quellen, laufend aktualisiert, mit Suche, Filter nach Quelle (Bildschirm, Logdatei, Log-Regel, Star-Citizen-Log, Telemetrie, Spielwerte lesen) und den Spalten Name, aktueller Wert, Quelle und letzte Änderung.

Die Namen gelten überall: in Ausgabevorlagen, Alarmen, Auslösern, Skripten und im Overlay-Designer. Auch die Ausgaben Nachschlagen, Namensprüfung, Munition, Geld und Timer schreiben ihr Ergebnis als Spielwert der Region (`<Region>.lookup`, `.namecheck`, `.ammo`, `.money`, `.timer`).

## Skripte

Für Sonderfälle gibt es einen Textschritt **Skript** in JavaScript, mit Editor, Beispielen und **Testen**. Skripte können Werte umrechnen, Log-Ereignisse zählen und Records an eine API veröffentlichen. Sie **rechnen nur**: Zugriff auf Dateien, Netzwerk oder andere Programme haben sie nicht.

## Spiele teilen

Gib Org-Mitgliedern deine Regionen, Listen, Modi und Log-Quellen in einer Datei.

1. Auf der Seite **Spiele** auf der Karte des Spiels **Teilen** und die `.fgwt-game.json` speichern.
2. Die Datei weitergeben, z. B. über Discord.
3. Die anderen klicken auf der Seite **Spiele** auf **Spiel importieren…** – die Datei wird ein neues Spiel mit allem darin.
4. Die ausführbare Datei steht nicht in der Datei, weil sie auf jedem PC woanders liegt: das importierte Spiel bearbeiten und die eigene `.exe` wählen.
5. **API-Token und Endpunkte stehen nie in der Datei.** Endpunkte gibst du getrennt unter **Einstellungen → Weitere APIs → Export…/Import…** weiter, ebenfalls ohne Token.

Andere Auflösung? Die Regionen passen sich an, wenn das Spiel zum ersten Mal auf dem neuen Monitor läuft – im Regionseditor prüfen.
