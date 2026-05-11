# Thermomanagement & Lüfter — Panasonic Lumix DC-S5IIX

## Übersicht

Die S5IIX verfügt über einen integrierten aktiven Kühllüfter — ein entscheidendes Unterscheidungsmerkmal zu den meisten anderen Kameras. Der Lüfter sitzt unter dem Suchergehäuse und ermöglicht zeitlich unbegrenzte Videoaufnahmen.

## Lüfter-Modi

Einstellung: **Setup-Menü > EIN/AUS > Lüfter Modus**

| Modus | Verhalten | Empfehlung |
|---|---|---|
| **AUTO1** | Lüfter startet proaktiv früh, priorisiert Kühlung | Für anspruchsvolle Formate (4K 60p, 4:2:2 10-Bit) |
| **AUTO2** | Lüfter startet nur bei steigender Temperatur | **Empfohlen für Kirchenstreaming** — guter Kompromiss |
| **FAST** | Lüfter läuft immer mit hoher Geschwindigkeit | Deutlich hörbar, für Streaming mit externem Mikrofon irrelevant |
| **NORMAL** | Mittlere Drehzahl | Leises Rauschen, kaum auf Tonspur hörbar |
| **SLOW** | Niedrige Drehzahl | Praktisch unhörbar, begrenzte Kühlleistung |
| **OFF** | Lüfter deaktiviert | **NUR für Fotomodus** — NICHT für Video/Streaming verwenden! |

### Empfehlung für Kirchenstreaming

**AUTO2** — Der Lüfter springt nur an, wenn die Temperatur steigt. Da in einer klimatisierten Kirche (18-25°C) die Temperatur typischerweise kein Problem darstellt, läuft der Lüfter selten oder gar nicht.

Wenn ein externes Mikrofon weit genug entfernt ist (>1-2m), ist selbst der Modus FAST unhörbar auf der Aufnahme. Da bei HDMI-Output das Kamera-Audio ohnehin nicht verwendet wird, ist Lüftergeräusch vollkommen irrelevant.

## Temperaturmanagement-Einstellung

Einstellung: **Setup-Menü > Monitor/Display 1 > Temperaturmanagement**

| Option | Verhalten |
|---|---|
| **STANDARD** | Kamera wird direkt angehalten, wenn Temperatur kritisch steigt |
| **HIGH** | Kamera darf verhältnismäßig warm werden — verlängert Aufnahmezeit |

### Empfehlung für Kirchenstreaming

**HIGH** — Diese Einstellung ist essenziell für Langzeit-Streaming. Die Kamera wird spürbar wärmer, was aber bei HDMI-Output auf einem Stativ kein Problem darstellt (man hält sie nicht in der Hand).

## Wärme-Reduktions-Maßnahmen

| Maßnahme | Wirkung |
|---|---|
| HDMI-Output OHNE interne Aufnahme | **Größte Einzelmaßnahme** — drastisch weniger Wärme |
| 1080p statt 4K über HDMI ausgeben | Weniger Prozessorlast, weniger Wärme |
| 25p statt 50p verwenden | Geringere Prozessorlast |
| IBIS ausschalten (Stativ!) | Leichte Wärmereduktion |
| LCD aufgeklappt lassen | Wirkt als zusätzliche Kühlfläche |
| Kein Cage/Gehäuse, das Lüftung blockiert | Luftzirkulation nicht behindern! |
| Kein direkte Sonneneinstrahlung auf Kamera | Offensichtlich, aber wichtig bei Outdoor-Events |

## Praxistest-Empfehlung

Vor dem ersten Live-Einsatz: Kamera mit finaler Konfiguration mindestens **60 Minuten** laufen lassen und Temperatur beobachten. Die S5IIX sollte bei:
- 25p FHD HDMI-Output + AUTO2 Lüfter + klimatisierter Raum
- **unbegrenzt** laufen können (3+ Stunden bestätigt)

## Warnsignale

- Thermometer-Symbol auf dem Display = Kamera nähert sich Grenze
- Bei "STANDARD"-Temperaturmanagement: Kamera schaltet ab!
- Bei "HIGH": Kamera arbeitet weiter, zeigt aber Warnung

## Zusammenfassung für Kirchenstreaming

```
Lüfter Modus:           AUTO2
Temperaturmanagement:    HIGH
Interne Aufnahme:        AUS (oder nur FHD als Backup)
IBIS:                    AUS (Stativ)
LCD:                     Aufgeklappt
HDMI-Output:             Bevorzugt 1080p25 oder 4K25
```
