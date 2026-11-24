# Star Citizen

[← Dokumentation](README.md)

Für Star Citizen liest die App zusätzlich die `Game.log` und den lokalen Telemetrie-Dienst des Spiels. Daraus entstehen die Module **Handel**, **Fracht**, **Verträge**, **Logbuch**, **Org live** und **Telemetrie**.

- [Voraussetzung: Star Citizen einrichten](#voraussetzung-star-citizen-einrichten)
- [Handel](#handel)
- [Fracht](#fracht)
- [Verträge und Blueprints](#verträge-und-blueprints)
- [Logbuch](#logbuch)
- [Telemetrie](#telemetrie)
- [Org live](#org-live)
- [Alte Logs einlesen](#alte-logs-einlesen)
- [Spielwerte aus der Game.log](#spielwerte-aus-der-gamelog)
- [Was das Spiel nicht loggt](#was-das-spiel-nicht-loggt)

## Voraussetzung: Star Citizen einrichten

1. Auf der Seite **Spiele** dein Star-Citizen-Spiel bearbeiten und mit **Durchsuchen…** seine `StarCitizen.exe` wählen – oder **Star Citizen** anhaken.
2. Unter **Einstellungen → Module** die gewünschten Module einschalten.

Die Star-Citizen-Module erscheinen nur, solange das aktive Spiel Star Citizen ist. Die `Game.log` ist automatisch als Log-Quelle eingetragen.

**LIVE und PTU getrennt:** Auf der Star-Citizen-Karte **Duplizieren**, dann in der Kopie die `StarCitizen.exe` des PTU wählen.

## Handel

**Handel** (Trading) liest die `Game.log`: Jeder Warenkauf wird mit seinem Verkauf zu einem Geschäft mit Gewinn zusammengeführt – nach *first in, first out*, je Spielsitzung, auch über Abstürze hinweg. Außer dem Spiel ist nichts einzurichten.

| Seite | Inhalt |
|---|---|
| **Laufender Handel** | Jedes Geschäft der Sitzung, ihr Gewinn und die noch offene Fracht; die obere Leiste zeigt den Gewinn ebenfalls |
| **Verlauf** | Frühere Sitzungen nach Zeitraum, mit Gewinndiagramm |
| **Märkte** | Einkaufs- und Verkaufsorte und Routen mit Gewinn pro SCU und pro Stunde – aus deinen eigenen Geschäften |
| **Waren** | Die Warennamen, nachgeschlagen auf star-citizen.wiki |

- **Teilverkäufe** teilen ein Geschäft; jeder Teil behält Kiosk, Menge und Preis.
- **Abgelehnte Käufe oder Verkäufe** (das Spiel meldet einen Fehler) werden wieder entfernt.
- **Fracht aus einer früheren Sitzung**, die du jetzt verkaufst, lässt sich ihrem Kauf zuordnen.
- **Verlorene Fracht** (zerstört, gestohlen): in ihrer Zeile **Als verloren markieren**, auf Wunsch mit Kommentar.
- **Shop-Artikel** zählen, sobald der Shop sie bestätigt hat.

**An FGWT senden:** unter **Einstellungen → FGWT** die Geschäfte einschalten. **Frühere Geschäfte an FGWT senden** steht im Kopf der Seite *Verlauf*. Die Handelsseite der FGWT-Website öffnet der Link *Handel* unter „Auf FGWT“. Zusätzlich kann ein [weiterer Endpunkt](fgwt-und-apis.md#weitere-apis) die Geschäfte bekommen, gewählt unter **Einstellungen → Handel**.

## Fracht

**Fracht** (Hauling) liest die angenommenen Frachtaufträge aus der `Game.log` und zeigt, was wohin noch zu liefern ist.

1. Frachtaufträge im Spiel annehmen. Aufträge, die wenige Sekunden nacheinander angenommen werden, bilden einen **Batch**. Den Abstand stellst du unter **Einstellungen → Fracht → Batch-Abstand (Sekunden)** ein (Standard 5).
2. Die Seite **Aufträge** zeigt den Batch: Ware nach Ziel mit den übrigen SCU (✓, wenn geliefert), die Summen und die Aufträge.
3. **Liefertabelle im Overlay zeigen, solange etwas zu liefern ist** unter **Einstellungen → Fracht** zeigt die Tabelle im Spiel. Die obere Leiste zeigt, wie viele Aufträge geliefert sind.
4. **Fracht planen** öffnet den **Frachtrechner** mit den Mengen des Batches: wie sie sich auf Kisten (32, 24, 16, 8, 4, 2 und 1 SCU) verteilen und ob sie nach Kapazität und Plätzen in das Frachtraster deines Schiffs passen.
5. Nächste Runde: **Neuen Batch beginnen**. Erledigte Aufträge verlassen die Tabelle, offene bleiben bis zu ihrem Ende.

**Hull-C-Reviews:** Für abgeschlossene Läufe kannst du ein Hull-C-Review (Auszahlungen, Kisten) ausfüllen und an FGWT senden; die Reviews der anderen Mitglieder liest die App von FGWT.

## Verträge und Blueprints

**Verträge** (Contracts) merkt sich jeden Vertrag mit Namen und Ausgang (abgeschlossen, fehlgeschlagen, abgebrochen, zurückgezogen, abgelaufen) und jeden erhaltenen Blueprint mit dem Vertrag, der ihn gab.

Eine eigene Seite in der App gibt es dafür nicht. Du siehst die Daten:

- auf der FGWT-Website unter **Missionen und Baupläne** (Link unter „Auf FGWT“),
- in der Zusammenfassung jeder Spielsitzung im [Logbuch](#logbuch),
- über einen [KI-Assistenten](ki-assistenten.md).

## Logbuch

Das **Logbuch** hält pro Spielsitzung fest, was das Spiel sagt: Shards, Ladezeiten, betretene Schiffe und die Zeit in jedem, Verletzungen und Behandlungen, Rechtsgebiete. Es hat die Seiten **Spielsitzungen** und **Schiffe**.

### Spielsitzungen als Brücke

**Logbuch → Spielsitzungen** zeigt die laufende Sitzung, während sie läuft, und jede frühere genauso.

- **Liste links:** Die laufende Sitzung ist grün markiert („Läuft gerade“). Jede Zeile hat zwei dünne Streifen für Spielläufe und Orte.
- **Kopf:** *Live* oder *Beendet*, Tag, Shards, eine große Uhr, Spielläufe, Abstürze, Ladezeit im Schnitt; rechts der Kontostand aus dem letzten Telemetrie-Frame.
- **Flugschreiber:** der Abend auf einer Zeitachse, eine Spur je Thema:
  - *Spiel* – Läufe, Laden heller, ein Kreuz für Absturz, Trennung oder Alt+F4, ein Strich fürs Beenden,
  - *Ort* – die Rechtsgebiete, die das Spiel nennt, z. B. microTech,
  - *Schiff* – eigene Schiffe hell, fremde lila,
  - *Ereignisse* – Verletzungen und Behandlungen,
  - *Heartbeat* – nur, solange die Sitzung läuft.
  Mit der Maus über einem Abschnitt steht da, was es ist und wann.
- **Heartbeat und Telemetrie:** was zuletzt an FGWT ging, wann, wie FGWT antwortete und wann der nächste Heartbeat fällig ist. *Der letzte Frame* klappt seinen Inhalt auf. Dafür müssen *Live-Status (Heartbeat)* und *Telemetrie an FGWT senden* unter **Einstellungen → FGWT** an sein.
- **Darunter:** die Zusammenfassung mit Start- und Endkontostand, Aktivitäten, Kommentar und **Fertig**, die Spielstarts mit *Hier teilen*, Schiffe, Verletzungen, Ladezeiten und Zonen.

Spielsitzungen lassen sich **teilen**, **zusammenführen** und **beenden**; der Handel folgt diesen Korrekturen, und FGWT erfährt sie ebenfalls.

Zu viel Bewegung neben dem Spiel? **Einstellungen → Allgemein → Animationen → Animationen abspielen** ausschalten.

### Overlay

Das Logbuch liefert ein Overlay-Widget mit dem **Zonenstatus**: Zonenart, Rechtsgebiet, Sperrgebiet, aktuelles Schiff und unbehandelte Verletzungen.

## Telemetrie

Star Citizen kann Programmen auf deinem PC sagen, wie es dir und deinem Schiff geht. Das Modul **Telemetrie** liest das, solange das Spiel läuft – als Spielwerte für Ausgaben, Alarme und Auslöser, als Kontostand für das Logbuch und auf einer eigenen Seite.

### Einschalten

1. Star Citizen einrichten (siehe oben) und **Telemetrie** unter **Einstellungen → Module** einschalten.
2. **Einstellungen → Telemetrie** zeigt die Zeile, die das Spiel in seiner `user.cfg` braucht – passend zu deinem Spielstand, für 4.10 z. B.:

   ```ini
   grpc.client.server.enabled = 1
   ```

   **In user.cfg eintragen** und bestätigen, oder die Zeile kopieren und selbst eintragen. Eine andere Zeile verändert die App nie.
3. Das Spiel starten oder neu starten – es liest die `user.cfg` nur beim Start. Sobald du im Universum bist, zeigt die Seite **Telemetrie** „Verbunden“ und was das Spiel sendet.

Unter **Einstellungen → Telemetrie → Wie oft** stellst du ein, wie oft pro Sekunde die App dem Strom folgt (1–10, Standard 4).

### Die Seite Telemetrie

Verbindungsstatus, der letzte Stand als aufklappbarer Baum, die letzte Minute einer gewählten Zahl, die Ereignisse, **Pause**, **Als JSON kopieren** und **Aufnehmen**. *Aufnehmen* schreibt alles, was das Spiel sendet, in den Ordner `telemetry` des Datenordners – hilfreich, wenn etwas falsch aussieht.

### Die 41 Werte

Alle Werte heißen `telemetry.<Name>`, z. B. `{telemetry.oxygen}` in einer Ausgabe oder ein Alarm auf `telemetry.hydrogenFuel`. Ja/Nein steht als `true`/`false`.

| Bereich | Werte |
|---|---|
| Spieler | `health`, `oxygen` (%), `hunger`, `thirst`, `bodyTemperature`, `heartRate`, `gravity`, `pressure`, `intoxication`, `outsideTemperature`, `radiation`, `breathable`, `locomotion` (`on foot`, `eva`, `seated`), `crewRole`, `seat`, `balance` |
| Schiff (nur im Sitz) | `ship`, `vehicleType`, `landed`, `gear`, `speed`, `verticalSpeed`, `altitude`, `radarAltitude`, `heading`, `hydrogenFuel` und `quantumFuel` (%, nur wenn das Spiel sie sendet), `boost` (%), `engines`, `lights`, `doorsLocked`, `coupled`, `cruise`, `warnings` (leuchtende Warnlampen, z. B. `PROX major`) |
| Waffen (nur im Sitz) | `weaponPreset`, `weapons`, `weaponsReady`, `decoys`, `noise`, `gimbalsLocked` |
| Ereignis | `event` – das letzte Ereignis für 5 Sekunden (`enter seat`, `leave seat`, `downed` …) |

Position, Missionen und Fracht kommen weiter aus der `Game.log`. Ändert sich der Kontostand, nimmt das Logbuch ihn als Start- und Endkontostand der Sitzung.

## Org live

**Org live** zeigt, wer aus der Org gerade spielt – wo, in welchem Schiff, wie es ihm geht – und welche Missionen geteilt werden. Die Daten kommen von FGWT.

1. Auf der FGWT-Website im Profil das **Teilen des Live-Status** einschalten. Nur Mitglieder, die das getan haben, erscheinen.
2. Der FGWT-Token braucht den Scope `live:read`. Ältere Tokens haben ihn nicht: auf der Website einen neuen erstellen und unter **Einstellungen → FGWT** speichern. *Test* zeigt dort unter *Was gelesen wird*, ob der Token ihn hat.
3. Die volle Übersicht ist die Live-Seite der Website: Link *Org live* unter „Auf FGWT“.
4. Im Spiel: unter **Einstellungen → Org live** das **Overlay-Widget** einschalten („Org · 3 online“ und die ersten 8 Mitglieder mit Ort und Schiff). Es fragt FGWT alle 15 Sekunden ab, nur solange es im Overlay ist und das Overlay sich zeigt.
5. Damit die anderen dich sehen: unter **Einstellungen → FGWT** die **Spielereignisse** einschalten. Ort, Schiff, Zustand und Missionen brauchen ihre jeweiligen Arten. **Einstellungen → Org live** sagt, was die anderen von dir nicht sehen, und schaltet es mit **Einschalten** ein.

## Alte Logs einlesen

**Einstellungen → Allgemein → Alte Logs** liest die Logs früherer Spielstarts (Ordner `logbackups` des Spiels) für jedes eingeschaltete Modul, das sie nutzt (Verträge, Handel, Logbuch). Was schon bekannt ist, bleibt, wie es ist. Nichts davon geht an FGWT.

## Spielwerte aus der Game.log

Ohne eigene Regel liefert die App für Star Citizen diese Spielwerte:

| Wert | Inhalt |
|---|---|
| `starcitizen.location` | Wo du zuletzt ein Inventar geöffnet hast, mit bekanntem Namen, z. B. *Everus Harbor* (der einzige Ort, den das Log nennt) |
| `starcitizen.locationId` | Derselbe Ort, wie das Log ihn nennt, z. B. `RR_HUR_LEO` |
| `starcitizen.shard` | Der Shard |
| `starcitizen.ship` | Das aktuelle Schiff |
| `starcitizen.jurisdiction` | Das Rechtsgebiet |
| `starcitizen.injuries` | Verletzungen, schlimmste zuerst, bis zu einem Medbett, einem Tod oder einer neuen Spielsitzung |

Was die App sonst noch von selbst aus der `Game.log` liest (Verträge, Fracht, Handel, Schiffe, Ort, Kampf, Verletzungen, Gesetz, Party, Blueprints, Sitzung), zeigt das Panel *Star Citizen liest* im [Log-Betrachter](spielwerte-lesen.md#log-betrachter).

## Was das Spiel nicht loggt

Manches schreibt Star Citizen nicht oder nicht zuverlässig in die `Game.log`, z. B. CrimeStat und Ruf. Das kann die App daher nicht aus dem Log zeigen. Den Kontostand liefert die [Telemetrie](#telemetrie); ohne Telemetrie kannst du ihn per [Geld-Ausgabe](spielwerte-lesen.md#beispiel-verdienst-der-sitzung) vom Bildschirm lesen oder in der Zusammenfassung eintippen.
