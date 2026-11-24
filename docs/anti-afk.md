# Anti-AFK

[← Dokumentation](README.md)

Solange das Spiel vorne ist und du nichts tust, bewegt **Anti-AFK** alle paar Sekunden die Maus in einem Muster, das dort endet, wo es begann, oder drückt eine deiner Tasten – damit das Spiel dich nicht abmeldet.

> **Hinweis:** Anti-AFK sendet Eingaben an das Spiel, als kämen sie von dir. Ob die Nutzungsbedingungen eines Spiels das erlauben und ob sein Anti-Cheat darauf reagiert, ist **nicht bekannt**. Die Nutzung geschieht **auf eigenes Risiko**.

## Einrichten

1. Anti-AFK unter **Einstellungen → Module** einschalten; anfangs ist es aus.
2. Den Hinweis auf der Seite **Anti-AFK** lesen und bestätigen. Ohne Bestätigung startet es nicht.
3. Wählen, was gesendet wird:
   - **Mausmuster** (Standard): Größe, Form (zufälliger Weg, Kreis, zur Seite und zurück) und Dauer einstellen. Die Größe zählt Mausbewegung, keine Bildschirmpixel; wie weit sich die Sicht dreht, hängt von deinen Mauseinstellungen ab – im Spiel ausprobieren.
   - **Tasten**: **Taste aufnehmen** und die Taste drücken. Nimm Tasten, die im Spiel nichts Schädliches tun – **nie Feuern oder Interagieren**.
4. Unter **Einstellungen → Tastenkürzel** einen Hotkey für **Anti-AFK starten oder anhalten** vergeben; anfangs hat es keinen. Das Overlay zeigt den Zustand und den Hotkey.

## Benutzen

Starte Anti-AFK auf der Seite oder per Hotkey und wechsle ins Spiel.

- Es sendet **nur an das erste Spielfenster**, das danach vorne ist, und **nur, solange es vorne ist**.
- Es sendet erst, wenn du das **Intervall lang** (anfangs 60 s) nichts getan hast.
- Ein anderes Fenster vorne **pausiert** es.
- Es **hält an**, wenn das Spiel endet, und ist beim Start der App **immer aus**.

### Spiel zurück nach vorne holen

Holen Popups das Spiel aus dem Vordergrund, setze den Haken **Spiel zurück nach vorne holen …**. Anti-AFK holt das Spiel dann zurück, wenn du kurz vor dem Wechsel nichts getan hast – höchstens dreimal pro Minute. <kbd>Alt</kbd>+<kbd>Tab</kbd> bleibt unberührt. Windows kann das Zurückholen ablehnen; die Seite zeigt das an.
