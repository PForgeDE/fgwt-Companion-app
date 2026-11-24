# FGWT und andere APIs

[← Dokumentation](README.md)

Die App kann Daten an die Web-API von [FGWT](https://fgwt.pforge.de/) und an beliebige weitere APIs senden. **Anfangs ist alles Senden aus.** Es geht nur, was du einschaltest.

- [Mit FGWT verbinden](#mit-fgwt-verbinden)
- [Spielereignisse](#spielereignisse)
- [Live-Status: Heartbeat und Telemetrie](#live-status-heartbeat-und-telemetrie)
- [Weitere APIs](#weitere-apis)
- [Records an eine andere API senden](#records-an-eine-andere-api-senden)
- [Eigene Records aus Regeln und Regionen](#eigene-records-aus-regeln-und-regionen)
- [Postausgang](#postausgang)

## Mit FGWT verbinden

1. Auf der FGWT-Website einen **API-Token** erstellen. Für Org live braucht er den Scope `live:read`.
2. In der App **Einstellungen → FGWT** öffnen, den Token eintragen und speichern. Er wird für dein Windows-Konto auf diesem PC verschlüsselt gespeichert.
3. **Test** prüft die Verbindung und zeigt unter *Was gelesen wird*, was der Token lesen darf.

Mit **Erweiterte Einstellungen zeigen** erscheinen Adresse, Zeitlimit und die Anfragen pro Teil.

Die Gruppe **Einstellungen → FGWT** hat diese Abschnitte:

| Abschnitt | Was gesendet wird |
|---|---|
| Verbindung | Token, Test |
| Spielereignisse | Was das Log über einen Spiellauf erzählt, als einzelne Ereignisse |
| Live-Status (Heartbeat) | Ein regelmäßiges Lebenszeichen, solange du spielst |
| Live-Status (Telemetrie) | Telemetrie-Frames aus dem Modul [Telemetrie](star-citizen.md#telemetrie) |

Dazu schickt der Handel seine Geschäfte, die Fracht ihre Hull-C-Reviews und das Logbuch seine Spielsitzungen, soweit jeweils eingeschaltet.

## Spielereignisse

Unter **Einstellungen → FGWT → Spielereignisse für FGWT** hat jede Kategorie einen Schalter, anfangs alle aus. Gesendet wird, was die `Game.log` über einen Spiellauf erzählt: Kills und Tode, Ausrüstung und Inventar, Frachtziele, Missionen, Blueprints, Fahrzeuge, Reisen, Gesundheit und die Sitzung selbst.

- Mit **Erweiterte Einstellungen zeigen** listet jede Kategorie ihre einzelnen Arten mit ihrer Anzahl; jede Art lässt sich einzeln ausschalten.
- Eine ausgeschaltete Art bleibt in der App gespeichert und wird nur nicht gesendet. Die Kategorie zeigt dann *teilweise an*.
- Eine neue Art folgt ihrer Kategorie, bis du sie ausschaltest.
- Ereignisse gehen in zeitlicher Reihenfolge an FGWT.

Die Spielereignisse sind auch die Grundlage dafür, dass andere Mitglieder dich in [Org live](star-citizen.md#org-live) sehen.

## Live-Status: Heartbeat und Telemetrie

**Heartbeat:** ein regelmäßiges Lebenszeichen an FGWT, solange du spielst. Das Intervall erscheint mit *Erweiterte Einstellungen zeigen*. Ein fälliger Heartbeat wartet, solange Telemetrie-Frames für denselben Spiellauf gehen.

**Telemetrie an FGWT senden:** schickt Frames aus dem Modul Telemetrie. Mit *Erweiterte Einstellungen zeigen* wählst du:

| Einstellung | Möglichkeiten |
|---|---|
| Weg | **Anfragen** (Standard, über den Postausgang) oder **Live-Verbindung** (WebSocket; Frames gehen ohne eigene Anfrage, solange die Verbindung steht) |
| Modus | mit jedem Update, gesammelt, nur der neueste, oder **bei Änderung**: ein Frame geht sofort, wenn sich etwas Wichtiges geändert hat (Sitz, Schiff, Fahrwerk, Warnlampen, Kontostand …), sonst der neueste alle N Sekunden |
| Sekunden | 1–30, Standard 5 |

Was zuletzt ging und wie FGWT antwortete, zeigt die Seite [Spielsitzungen](star-citizen.md#spielsitzungen-als-brücke) im Logbuch.

## Weitere APIs

Neben FGWT kannst du eigene Endpunkte anlegen, z. B. die API einer anderen Org.

1. **Einstellungen → Weitere APIs → Endpunkt hinzufügen.**
2. Name (z. B. „Org-API“), Basis-URL und, falls nötig, Token eintragen. **Speichern** verschlüsselt den Token für dein Windows-Konto.
3. **An diesen Endpunkt senden** anhaken.

Mit **Erweiterte Einstellungen zeigen** erscheinen: ein Schlüssel in einem Header statt eines Tokens, Zeitlimit, Art der Anmeldung, die **Zuordnungen** (Mappings) sowie **Export…** und **Import…**. Export und Import enthalten nie Tokens; importierte Endpunkte sind ausgeschaltet, bis du die Adresse geprüft und deinen eigenen Token eingetragen hast.

## Records an eine andere API senden

Alles, was die App aufzeichnet – Geschäfte, Spielsitzungen, Hull-C-Reviews, Spielereignisse –, kann ohne Skript an eine weitere API gehen.

1. Unter **Einstellungen → Weitere APIs** die API wählen. Unter *Records, die sie nimmt* stehen ihre Zuordnungen: welcher Record, welche Anfrage (Methode, Pfad, Body, Key).
2. Nimmt die API dieselben Anfragen wie FGWT: **Kopieren, was FGWT bekommt** – die Zuordnungen von FGWT werden ausgeschaltet hinzugefügt. Sonst **Zuordnung hinzufügen**, den Record wählen und Pfad und Body schreiben.

   | Platzhalter | Bedeutung |
   |---|---|
   | `{record.price}` | Ein Feld des Records |
   | `{key}` | Sein eindeutiger Schlüssel |
   | `{game}` | Sein Spiel |
   | `{client}` | Diese Installation |

3. Die **Vorschau** zeigt die Anfrage für ein Beispiel und was noch falsch ist.
4. **Test senden** schickt die Beispielanfrage einmal, nach Rückfrage. Achtung: Eine API, die speichert, was sie bekommt, speichert auch das.
5. Die Zuordnung einschalten, um zu senden.

## Eigene Records aus Regeln und Regionen

Auch eine [Log-Regel](spielwerte-lesen.md#log-regeln) oder eine Region kann Records erzeugen, die du per Zuordnung an eine API sendest.

1. Bei einer Log-Regel unter *Erzeugt* **API-Record** anhaken; bei einer Region im Reiter *Ausgabe* **Record erzeugen, wenn sich die Werte ändern**.
2. Der Record-Typ heißt `custom.<Name>` (Kleinbuchstaben, Ziffern, `-` und `_`).
3. **Felder des Records** wählen; leer nimmt alle. Jeder Record hat außerdem `text`, `time` (UTC) und `source`.
4. Eine Regel erzeugt einen Record je Treffer, eine Region nur, wenn sich ihre Werte geändert haben. Beim Start erneut gelesene Einträge zählen nur mit **Auch aus wiederholten Einträgen**.
5. Der **Key** verhindert Doppelte: ein erneut gelesener Eintrag ergibt denselben Key und wird nicht noch einmal gesendet.
6. Unter **Einstellungen → Weitere APIs** eine Zuordnung des Typs anlegen, z. B. `custom.kills` → `POST api/kills` mit dem Body `{"victim": "{record.victim}"}`, und einschalten.

Auch [Skripte](spielwerte-lesen.md#skripte) können Records veröffentlichen.

## Postausgang

Jede Anfrage an FGWT oder eine andere API geht über den **Postausgang** (Outbox, Icon unten in der Seitenleiste).

- Ohne Verbindung wartet eine Anfrage und wird erneut versucht, **auch nach einem Neustart** der App.
- Jede Anfrage hat einen eindeutigen Schlüssel, damit sie beim Wiederholen nicht doppelt ankommt.
- Eine Anfrage, die die API ablehnt, steht mit dem Grund als *fehlgeschlagen* in der Liste.
