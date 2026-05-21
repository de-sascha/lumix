# Vorfall-Bericht: Unerwartetes Abschalten der S5IIX im Stream

**Datum:** Mai 2026
**Firmware:** 2.6
**Setup:** S5IIX, HDMI-Out auf OBS-PC, Kirchen-Streaming

## Symptom

Die Kamera ging während eines Gottesdienst-Streams unerwartet aus. Kein Vorwarn-Symbol (kein Thermometer), keine erkennbare Ursache am Kabel oder Netzteil.

## Diagnose

Beim systematischen Durchgehen der Energiespar-Einstellungen stellte sich heraus:

| Einstellung | Wert zum Zeitpunkt des Vorfalls |
|---|---|
| Ruhemodus | **5 Min** (Werks-Default) |
| Ruhemodus (Wi-Fi) | EIN |
| Sucher (LVF) | 5 Min |

Die Kamera erkennt **HDMI-Output alleine NICHT zuverlässig als „Aktivität"**, obwohl das Handbuch das Gegenteil suggeriert. Wenn die Kamera auf dem Stativ steht, niemand sie anfasst und keine interne Aufnahme läuft, greift der Ruhemodus nach 5 Minuten und schaltet die Kamera ab.

## Lösung — Vorher / Nachher

| Einstellung | Vorher | Nachher | Begründung |
|---|---|---|---|
| Ruhemodus | 5 Min | **AUS** | Hauptursache des Vorfalls |
| Ruhemodus (Wi-Fi) | EIN | **AUS** | Zweiter unabhängiger Trigger |
| Sucher (LVF) | 5 Min | **AUS** | Sicherheitshalber, Sucher wird nicht genutzt |
| Energiespar-Sucheraufn. → Zeit bis zur Ruhe | OFF | OFF | War schon korrekt |
| Ruhe-Modus Aktivierung | Control Panel | Control Panel | Mit Ruhemodus=AUS irrelevant |
| Lüfter Modus | AUTO2 | AUTO2 | Bereits optimal |
| **Temperaturmanagement** | STANDARD | **HIGH** | Verlängert Aufnahmezeit, Kamera darf wärmer werden |

## Lessons Learned

1. **Werks-Defaults sind nicht Streaming-tauglich.** Ruhemodus=5 Min ist der Standard und muss aktiv abgeschaltet werden.
2. **Handbuch-Aussagen kritisch prüfen.** Das Handbuch behauptet, HDMI-Output deaktiviere Power Save automatisch. In der Praxis stimmt das nicht zuverlässig.
3. **Mehrere Trigger gleichzeitig.** „Ruhemodus", „Ruhemodus Wi-Fi" und „Sucher LVF" sind unabhängig — alle müssen einzeln auf AUS.
4. **Doppel-Sicherung sinnvoll.** Internes FHD-Backup-Recording hält die Kamera „beschäftigt" UND liefert ein Backup-Video.

## Verifikations-Tests (nach der Korrektur)

- [ ] **Mini-Test (15 Min):** Kamera aufbauen, nicht anfassen, prüfen ob sie an bleibt
- [ ] **Hitzetest (2-3h):** Dauerlauf in Streaming-Konfiguration, Thermik beobachten
- [ ] **Real-Test:** Erster Gottesdienst nach Korrektur — beobachten

## Konfigurations-Pfad zur Schnellprüfung

```
MENU → 🔧 Setup → EIN/AUS → Sparmodus
```

Dort alle Werte gegen die „Nachher"-Spalte oben abgleichen.

## Confidence

⚠️ Hoch — Vorfall reproduzierbar erklärbar durch Werks-Default. Die FW 2.6 zeigt das Verhalten konsistent. Korrektur in der Praxis noch zu verifizieren (15-Min-Test ausstehend).
