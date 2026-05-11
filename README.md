# Lumix S5IIX Church Streaming Knowledge Base

Umfassende Wissensbasis für den Einsatz der Panasonic Lumix DC-S5IIX im Kirchenstreaming mit OBS Studio.

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
