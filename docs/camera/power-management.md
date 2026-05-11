# Stromversorgung & Standby-Vermeidung — Panasonic Lumix DC-S5IIX

## USB Power Delivery (USB-PD)

Die S5IIX unterstützt USB-PD über den USB-C-Anschluss. Das ermöglicht Dauerbetrieb bei gleichzeitigem Laden des eingelegten Akkus.

### Technische Anforderungen

| Parameter | Wert |
|---|---|
| USB-PD Profil | 9V / 3A (27W) Minimum |
| Anschluss | USB-C (am Kameragehäuse) |
| Verhalten | Kamera läuft über USB-PD, Akku wird gleichzeitig geladen |
| Failover | Bei USB-Trennung nahtloser Wechsel auf Akku |

### Empfohlene Netzteile

- Mindestens 30W USB-PD Netzteil mit 9V/3A Profil
- Kurzse, hochwertige USB-C Kabel (zertifiziert für PD)
- Beispiele: Anker Nano 30W, Apple 30W USB-C, RAVPower 30W PD

### Wichtige Hinweise aus dem Handbuch

- Akku muss eingelegt sein (Kamera funktioniert NICHT ohne Akku über USB-PD)
- Laden dauert bei eingeschalteter Kamera länger als bei ausgeschalteter
- Nicht über USB-Hubs oder Tastatur-USB-Ports anschließen
- Bei USB-PD-inkompatiblen Geräten: nur Stromversorgung, kein Laden
- Akkustand kann trotz USB-PD unter bestimmten Bedingungen sinken (hohe Last)

## Standby/Sleep-Vermeidung

### Kritische Einstellungen

Einstellung: **Setup-Menü > Monitor/Display 1 > Power Save Mode**

| Einstellung | Empfehlung für Streaming | Menüpfad |
|---|---|---|
| Sleep Mode | **OFF** | Setup > Monitor/Display 1 > Power Save Mode |
| Sleep Mode (Wi-Fi) | **OFF** | Setup > Monitor/Display 1 > Power Save Mode |
| Auto LVF/Monitor Off | **OFF** | Setup > Monitor/Display 1 > Power Save Mode |
| Power Save LVF Shooting | **OFF** | Setup > Monitor/Display 1 > Power Save Mode |

### Power Save Mode ist AUTOMATISCH DEAKTIVIERT bei:

Laut offiziellem Handbuch ist Power Save Mode nicht aktiv in folgenden Fällen:
- Während Videoaufnahme/Videowiedergabe
- Bei PC-Verbindung
- Bei Time Lapse Shot
- Bei Stop Motion Animation (Auto Shooting)
- Bei Live View Composite
- Bei Focus Transition
- Während Slide Show
- **Während HDMI-Output für Aufnahme**

**Wichtig:** HDMI-Output hält die Kamera wach! Trotzdem alle Sleep-Modi explizit ausschalten als Sicherheitsnetz.

## Empfohlenes Power-Setup für Kirchenstreaming

### Primär: USB-PD + Akku als USV

```
┌─────────────────┐     USB-C     ┌─────────────┐
│ 30W USB-PD      │───────────────│ S5IIX       │
│ Netzteil        │               │ (Akku BLK22 │
│ (an Steckdose)  │               │  eingelegt)  │
└─────────────────┘               └─────────────┘
```

**Vorteile:**
- Unbegrenzte Laufzeit
- Akku als automatische USV (jemand stolpert über Kabel → kein Ausfall)
- Ein voller BLK22 gibt ca. 70-90 Min. Video-Backup

### Alternative: DC-Koppler DMW-DCC17 (Dummy-Akku)

```
┌─────────────────┐     DC        ┌─────────────┐
│ AC-Adapter +    │───────────────│ S5IIX       │
│ DC-Koppler      │               │ (kein Akku) │
│ DMW-DCC17       │               │             │
└─────────────────┘               └─────────────┘
```

**Vorteile:**
- Garantiert unbegrenzte Laufzeit
- Kein Akku-Wärme-Problem

**Nachteile:**
- KEIN Failover bei Stromausfall → Kamera schaltet sofort ab!
- Batteriefach schließt nicht komplett (kosmetisch)

### Dritte Option: Battery Grip DMW-BGS5

- Nimmt zweiten BLK22-Akku auf
- Kein USB-PD-Passthrough (USB muss an Kameragehäuse)
- 2x BLK22 ≈ 2,5-3 Stunden HDMI-Output
- Nur sinnvoll wenn USB-PD nicht möglich ist

## Empfehlung

**USB-PD mit eingestecktem vollgeladenem Akku** — die zuverlässigste Lösung:
- Dauerbetrieb garantiert
- Automatisches Failover bei Stromunterbrechung
- Prüfen ob Akku auf >50% bleibt während des Betriebs (sonst stärkeres Netzteil verwenden)

## Checkliste vor dem Gottesdienst

- [ ] USB-PD Netzteil angeschlossen und Kamera zeigt Lade-Symbol
- [ ] Akku BLK22 voll geladen eingelegt
- [ ] Sleep Mode: OFF
- [ ] Auto LVF/Monitor Off: OFF
- [ ] HDMI-Kabel fest angeschlossen
- [ ] 10-Minuten-Test: Kamera bleibt wach
