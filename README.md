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
- [Vorfall-Bericht: Kamera ging im Stream aus (Mai 2026)](docs/camera/standby-incident-2026-05.md) — Diagnose Ruhemodus-Default, Vorher/Nachher-Konfiguration
- [Videoeinstellungen](docs/camera/video-settings.md) — Systemfrequenz, Codec/Bitrate, Bildrate, 180°-Shutter-Regel, Bildstil
- [Autofokus-Einstellungen](docs/camera/af-settings.md) — AF-Modi für Kirche, Gesichts-/Augenerkennung, Hunting-Vermeidung, Szenarien
- [HDMI-Output](docs/camera/hdmi-output.md) — Clean HDMI, 4K vs 1080p, Farbtiefe, Kabel-Empfehlungen

### OBS Studio & Capture
- [Encoder-Einstellungen (NVENC AV1)](docs/obs/encoder-settings.md) — AV1 10Mbps p6, Szenen-Konfiguration, Bandbreiten-Planung
- [Blackmagic DeckLink Setup](docs/obs/blackmagic-setup.md) — Desktop Video Konfiguration, SDI/HDMI, OBS-Integration
- [Szenen-Konfiguration (Hosanna)](docs/obs/scene-config.md) — Signal-Flow, Scene Collection, NDI-Workflow, S5IIX-Integration

### Objektive
- [Samyang AF 35-150mm F2-2.8](docs/lenses/samyang-35-150.md) — Hauptobjektiv, AF-Verhalten, optimale Einstellungen, Einschränkungen
- [Panasonic Lumix S 18-40mm F4.5-6.3](docs/lenses/lumix-18-40.md) — Kit-Objektiv, Lichtschwäche-Analyse, nur für Weitwinkel-Backup

### Streaming & Netzwerk
- [Netzwerk-Architektur & NDI](docs/streaming/network-config.md) — LAN-Setup, NDI-Praxis, Signal-Formate, Multi-Cam-Planung
- [Best Practices Langzeit-Streaming](docs/streaming/best-practices.md) — Vor-Ort-Checkliste, Belichtungsstrategie, Dual Native ISO, Audio, Wartung

---

## Setup-Überblick

| Komponente | Detail |
|---|---|
| Kamera (neu) | Panasonic Lumix DC-S5IIX (Gehäuse-FW 2.6, Dez. 2025) — SN: WJ5DC001118 |
| Objektiv-Firmware | Samyang AF 35-150mm F2-2.8 — FW 3.6 |
| Kamera (aktuell) | Panasonic AW-HE40HW PTZ (SDI → DeckLink) |
| Capture Card | Blackmagic DeckLink Mini Recorder 4K (SDI für PTZ, HDMI für S5IIX) |
| Software | OBS Studio 32.1.2 (Windows 11 Pro) |
| Encoder | NVIDIA NVENC AV1 (RTX 4060, 10 Mbps, p6) |
| Audio | Focusrite Scarlett 2i2 USB (WASAPI, 48 kHz, +60 ms Offset) |
| NDI | DistroAV v6.2.1 — Beamer PC (SongBeamer) → OBS |
| Objektiv 1 | Samyang AF 35-150mm F2-2.8 (L-Mount) |
| Objektiv 2 | Panasonic Lumix S 18-40mm F4.5-6.3 (Kit) |
| Netzwerk | Gigabit LAN, Vodafone Cable (1Gb/50Mbit Up) |
| Einsatz | Kirchengottesdienste Hosanna (1-3h, variable Beleuchtung) |

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
│   ├── encoder-settings.md        # NVENC AV1 Optimierung (Hosanna Praxis)
│   ├── blackmagic-setup.md        # DeckLink Desktop Video Setup (SDI/HDMI)
│   └── scene-config.md            # Szenen, Signal-Flow, NDI, S5IIX-Integration
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
