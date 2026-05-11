# Lumix S5IIX Church Streaming Knowledge Base

Umfassende Wissensbasis für den Einsatz der Panasonic Lumix DC-S5IIX im Kirchenstreaming mit OBS Studio.

---

## Inhaltsverzeichnis

### Schnellstart
- [Schnellstart-Anleitung Sonntagsgottesdienst](docs/QUICK-START.md) — 60-Min-Countdown, Checkliste, Notfall-Karte

### Kamera
- [Firmware-Changelog & EU-Einschränkungen](docs/camera/firmware-changelog.md) — Versionshistorie v1.0–v3.7, regionale Unterschiede, Verifikations-Checkliste
- [Thermomanagement & Lüfter](docs/camera/thermal-management.md) — Lüfter-Modi (AUTO1/2, FAST, SLOW, OFF), Temperaturmanagement-Einstellung, Wärme-Reduktion
- [Stromversorgung & Standby-Vermeidung](docs/camera/power-management.md) — USB-PD Anforderungen, Sleep-Modi deaktivieren, Akku als USV
- [Videoeinstellungen](docs/camera/video-settings.md) — Systemfrequenz, Codec/Bitrate, Bildrate, 180°-Shutter-Regel, Bildstil
- [Autofokus-Einstellungen](docs/camera/af-settings.md) — AF-Modi für Kirche, Gesichts-/Augenerkennung, Hunting-Vermeidung, Szenarien
- [HDMI-Output](docs/camera/hdmi-output.md) — Clean HDMI, 4K vs 1080p, Farbtiefe, Kabel-Empfehlungen

### OBS Studio & Capture
- [Encoder-Einstellungen (NVENC)](docs/obs/encoder-settings.md) — H.264/HEVC, CBR-Bitrate, Szenen-Konfiguration, Bandbreiten-Planung
- [Blackmagic DeckLink Setup](docs/obs/blackmagic-setup.md) — Desktop Video Konfiguration, OBS-Integration, Troubleshooting

### Objektive
- [Samyang AF 35-150mm F2-2.8](docs/lenses/samyang-35-150.md) — Hauptobjektiv, AF-Verhalten, optimale Einstellungen, Einschränkungen
- [Panasonic Lumix S 18-40mm F4.5-6.3](docs/lenses/lumix-18-40.md) — Kit-Objektiv, Lichtschwäche-Analyse, nur für Weitwinkel-Backup

### Streaming & Netzwerk
- [Netzwerk-Architektur](docs/streaming/network-config.md) — LAN-Setup, HDMI vs NDI vs SRT, Multi-Cam-Planung, Bandbreiten-Kalkulation
- [Best Practices Langzeit-Streaming](docs/streaming/best-practices.md) — Vor-Ort-Checkliste, Belichtungsstrategie, Dual Native ISO, Audio, Wartung

---

## Setup-Überblick

| Komponente | Detail |
|---|---|
| Kamera | Panasonic Lumix DC-S5IIX (Firmware 2.6, Dez. 2025) |
| Capture Card | Blackmagic DeckLink Mini Recorder 4K |
| Software | OBS Studio (Windows 11) |
| Objektiv 1 | Samyang AF 35-150mm F2-2.8 (L-Mount) |
| Objektiv 2 | Panasonic Lumix S 18-40mm F4.5-6.3 (Kit) |
| Netzwerk | Gigabit LAN, Vodafone Cable (1Gb/50Mbit Up) |
| Einsatz | Kirchengottesdienste (1-3h, variable Beleuchtung) |

## Dokumentationsstruktur

```
docs/
├── camera/
│   ├── firmware-changelog.md      # Firmware-Historie & EU-Einschränkungen
│   ├── thermal-management.md      # Überhitzungsschutz & Lüfter
│   ├── power-management.md        # USB-PD, Dauerbetrieb, Standby-Vermeidung
│   ├── video-settings.md          # Videoformate, Bildrate, Codec
│   ├── af-settings.md             # Autofokus-Konfiguration für Kirche
│   └── hdmi-output.md             # HDMI-Clean-Output-Einstellungen
├── obs/
│   ├── encoder-settings.md        # NVENC-Optimierung
│   ├── blackmagic-setup.md        # DeckLink Desktop Video Setup
│   └── scene-config.md            # Szenen-Konfiguration
├── lenses/
│   ├── samyang-35-150.md          # Samyang AF 35-150mm F2-2.8
│   └── lumix-18-40.md             # Panasonic S 18-40mm Kit
├── streaming/
│   ├── network-config.md          # LAN/NDI/SRT Setup
│   └── best-practices.md          # Langzeit-Streaming Empfehlungen
└── QUICK-START.md                 # Schnellstart-Anleitung Sonntagsgottesdienst
```

## Region

EU-Modell (Deutschland). Alle Angaben beziehen sich auf die EU-Firmware.

## Systemfrequenz

**50,00 Hz (PAL)** — Pflicht in der EU wegen 50Hz-Netzfrequenz. Verfügbare Bildraten: 25p, 50p, 100p.
