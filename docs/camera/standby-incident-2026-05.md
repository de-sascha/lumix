# Kapitel 16 — Vorfall: Kamera ging im Stream aus (Mai 2026)

> Teil V, Kapitel 16 des [S5IIX-Handbuchs](../../README.md). Verwandt: [4. Stromversorgung und Standby](power-management.md).

## Worum geht es hier?

Im Mai 2026 hat sich die S5IIX **mitten im Hosanna-Gottesdienst-Stream selbst abgeschaltet**. Kein erkennbares Problem an Strom, Kabel oder Hitze — die Kamera war einfach aus. Dieses Kapitel dokumentiert den Vorfall samt Diagnose und der daraus abgeleiteten Standard-Konfiguration. **Damit das Gleiche nicht noch mal passiert.**

> **Zusammenfassung in einem Satz:** Der Werks-Default des Ruhemodus (5 Min) hat die Kamera trotz aktiver HDMI-Ausgabe ausgeschaltet — entgegen der Aussage des Panasonic-Handbuchs.

---

## 16.1 Eckdaten

| Feld | Wert |
|---|---|
| Datum | Mai 2026 |
| Firmware-Stand | 2.6 |
| Setup zum Zeitpunkt | S5IIX → HDMI → DeckLink → OBS-PC |
| Einsatz | Kirchen-Streaming Hosanna |

## 16.2 Was passiert ist

Die Kamera ging während des Streams **unerwartet aus**. Es gab kein Vorwarn-Symbol, insbesondere kein Thermometer-Symbol — also keine Hitze-Warnung. Kabel waren gesteckt, USB-PD-Netzteil lief. Trotzdem: schwarzes Bild im Stream, Kamera komplett aus.

## 16.3 Diagnose

Die Diagnose erfolgte durch systematisches Durchgehen der Energiespar-Einstellungen. Diese Werte waren zum Zeitpunkt des Vorfalls aktiv:

| Einstellung | Wert beim Vorfall |
|---|---|
| Ruhemodus | **5 Min** (Werks-Default) |
| Ruhemodus (Wi-Fi) | EIN |
| Sucher (LVF) | 5 Min |

### Was ist tatsächlich schiefgelaufen?

Das Panasonic-Handbuch behauptet, der Ruhemodus werde während HDMI-Ausgabe für Aufnahme **automatisch deaktiviert**. In unserem Setup hat das nicht funktioniert: Die Kamera hat HDMI-Output **alleine nicht zuverlässig als „aktive Aufnahme"** erkannt. Da sie zudem auf dem Stativ stand, niemand sie anfasste und keine interne Aufnahme lief, hat der Ruhemodus nach 5 Minuten zugeschlagen und die Kamera abgeschaltet.

**Die wahrscheinliche technische Ursache:** Eine externe Capture-Karte wie die DeckLink sendet der Kamera offenbar nicht das Signal, das die Kamera als „aktive HDMI-Aufnahme" interpretieren würde. Die Kamera „sieht" sich also selbst als untätig — und folgt brav ihrem Werks-Default.

---

## 16.4 Lösung — Vorher / Nachher

Alle Spar-Trigger einzeln **explizit auf AUS**, plus Temperaturmanagement auf HIGH:

| Einstellung | Vorher | Nachher | Begründung |
|---|---|---|---|
| Ruhemodus | 5 Min | **AUS** | Hauptursache des Vorfalls |
| Ruhemodus (Wi-Fi) | EIN | **AUS** | Zweiter unabhängiger Trigger |
| Sucher (LVF) | 5 Min | **AUS** | Sicherheitshalber, Sucher wird nicht genutzt |
| Energiespar-Sucheraufn. → Zeit bis zur Ruhe | OFF | OFF | War schon korrekt |
| Ruhe-Modus Aktivierung | Control Panel | Control Panel | Mit Ruhemodus=AUS irrelevant |
| Lüfter Modus | AUTO2 | AUTO2 | Bereits optimal |
| **Temperaturmanagement** | STANDARD | **HIGH** | Verlängert die zulässige Aufnahmezeit deutlich, damit das nicht der nächste Stolperstein wird |

### Schnellprüfung — wo finde ich diese Einstellungen?

```
MENU → 🔧 Setup → EIN/AUS → Sparmodus
```

Dort alle Werte gegen die „Nachher"-Spalte abgleichen.

---

## 16.5 Lessons Learned

Vier Erkenntnisse aus dem Vorfall, die in unsere Standard-Konfiguration eingeflossen sind:

1. **Werks-Defaults sind nicht Streaming-tauglich.** Ruhemodus = 5 Min ist Auslieferungszustand und muss aktiv abgeschaltet werden.
2. **Handbuch-Aussagen kritisch prüfen.** Der Satz „HDMI-Output deaktiviert Power Save automatisch" stimmt in unserem Setup nicht zuverlässig. Wir verlassen uns nicht auf solche Aussagen, sondern schalten lieber alles selbst aus.
3. **Mehrere Trigger gleichzeitig.** „Ruhemodus", „Ruhemodus Wi-Fi" und „Sucher LVF" sind drei unabhängige Schalter. Es reicht nicht, einen davon auszuschalten — alle drei müssen einzeln auf AUS.
4. **Doppel-Sicherung lohnt sich.** Eine zusätzlich mitlaufende interne FHD-Aufnahme hält die Kamera „beschäftigt" und liefert obendrein ein Backup-Video. Mehr dazu in [Kapitel 4.3](power-management.md#43-doppel-sicherung-internes-backup-recording).

---

## 16.6 Verifikations-Tests nach der Korrektur

So wird geprüft, ob die Korrektur wirklich greift:

- [ ] **Mini-Test (15 Min):** Kamera fertig konfiguriert aufbauen, **nicht anfassen**, prüfen ob sie die ganzen 15 Minuten an bleibt.
- [ ] **Hitzetest (2–3 h):** Dauerlauf in Streaming-Konfiguration, Thermometer-Symbol beobachten. *(Schon bestanden am 2026-05-21: 2× 3,5 h 4K-Daueraufnahme, siehe [Kapitel 5.5](thermal-management.md#55-praxistest-empfohlen--bevor-es-live-geht).)*
- [ ] **Real-Test:** Erster Gottesdienst nach der Korrektur — beobachten, ob die Kamera durchhält.

---

## 16.7 Confidence

**Hoch** — der Vorfall ist reproduzierbar erklärbar durch den Werks-Default. Die FW 2.6 zeigte das Verhalten konsistent. Unter FW 2.7 ist das Verhalten technisch identisch, da am Sparmodus-System nichts geändert wurde. Die finale Bestätigung im Real-Einsatz steht zum Zeitpunkt der letzten Aktualisierung dieses Kapitels noch aus.
