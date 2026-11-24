# Overlay und Overlay-Designer

[← Dokumentation](README.md)

## Das Overlay

Das Overlay ist ein Fenster, das immer über dem Spiel liegt und Klicks zum Spiel durchlässt. Es zeigt:

- die Ausgaben deiner Regionen, als Liste oder als Beschriftung **neben der Region**,
- Widgets anderer Module, z. B. Handelsgewinn, Liefertabelle, Zonenstatus, Org live, Anti-AFK-Zustand,
- die Checkliste des aktiven Modus,
- die Tafeln aus dem [Overlay-Designer](#overlay-designer).

| Taste | Wirkung |
|---|---|
| <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>O</kbd> | Overlay zeigen / verbergen |
| <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>L</kbd> | Overlay entsperren, um es zu verschieben, und wieder sperren |
| <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>B</kbd> | Regionsrahmen auf dem Bildschirm zeigen |

Alle Tasten: [Tastenkürzel](tastenkuerzel.md).

**Wann das Overlay sichtbar ist:** Es verschwindet, solange das Spiel nicht im Vordergrund ist (oben steht dann „Spiel nicht im Vordergrund“) und solange das Scannen pausiert ist. Es listet nur Regionen des aktiven Modus, bei denen **Im Overlay anzeigen** an ist. Star Citizen im Vollbild ist kein Problem.

Aussehen und Verhalten stellst du unter **Einstellungen → Overlay und Alarme** ein.

### Streams und Aufnahmen

Overlay, Beschriftungen und Regionsrahmen werden **absichtlich aus Bildschirmaufnahmen herausgehalten**. So landen sie nie in dem, was die App selbst liest, und deine Zuschauer sehen das saubere Spiel. Im Stream oder in einem Screenshot fehlt das Overlay daher.

## Overlay-Designer

Mit dem **Overlay-Designer** baust du eigene Tafeln ins Overlay. Jede Tafel sitzt an ihrem Platz und zeigt Zeilen aus Spielwerten jeder Quelle – Bildschirm-Regionen, Log-Regeln, das Star-Citizen-Log und die Telemetrie –, auch gemischt in einer Zeile, etwa:

```text
{telemetry.speed} m/s · {Cargo.used} SCU
```

### Zeilenarten

| Art | Inhalt |
|---|---|
| **Text** | Eine Textvorlage mit Spielwerten, wie bei der [Text-Ausgabe](spielwerte-lesen.md#textvorlagen) |
| **Balken** | Ein Wert gegen einen vollen Wert, nach Schwellen gefärbt |
| **Block** | Der Overlay-Teil eines anderen Moduls, z. B. von Handel |

Eine Zeile wird neu gezeichnet, wenn sich einer ihrer Werte ändert – höchstens so oft wie eingestellt.

### Eine Tafel bauen

1. **Overlay-Designer** öffnen (Modul unter *Einstellungen → Module* einschalten) und **Tafel hinzufügen**.
2. Einen Text oder Balken hinzufügen und Werte aus der Liste wählen; die Tags zeigen, woher jeder Wert kommt.
3. Den Monitor wählen und **Auf dem Bildschirm bearbeiten**: Tafeln an ihren Platz ziehen, Zeilen zwischen Tafeln verschieben; <kbd>Esc</kbd> schließt den Editor.
4. Optional unter **Zeigen, wenn** eine Bedingung hinzufügen, z. B. `screenreading.mode` ist *Mining*.

Tafeln und Zeilen können außerdem **je Layout einen eigenen Platz** haben oder **an einer Region verankert** sein.

### Ausgaben der Regionen übernehmen

Unter **Ausgaben der Regionen** → **In eine Tafel übernehmen** ziehen die Ausgaben deiner Regionen in eine Designer-Tafel um. Das lässt sich auch wieder zurückgeben.
