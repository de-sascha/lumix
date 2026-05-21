# Panasonic Lumix DC-S5IIX — Benutzerhandbuch

Ein durchgängig lesbares Handbuch zur Panasonic Lumix DC-S5IIX, mit Schwerpunkt auf dem konkreten Einsatz im Kirchenstreaming (Hosanna) — aber so aufgebaut, dass es Schritt für Schritt zu einer kompletten S5IIX-Referenz für Einsteiger wächst.

> **Für wen ist das?** Geschrieben für Anwender, die nicht aus der Foto-/Video-Profi-Welt kommen. Fachbegriffe werden bei der ersten Verwendung erklärt. Wer schnell etwas nachschlagen will, springt direkt über das Inhaltsverzeichnis.

---

## Inhaltsverzeichnis

- [Über dieses Handbuch](#über-dieses-handbuch)
- [Schnellstart](#schnellstart)
- [Teil I — Grundlagen](#teil-i--grundlagen)
  - [1. Mein Setup](#1-mein-setup)
  - [2. Region und Systemfrequenz](#2-region-und-systemfrequenz)
  - [3. Firmware-Stand](#3-firmware-stand)
- [Teil II — Die Kamera einrichten](#teil-ii--die-kamera-einrichten)
  - [4. Stromversorgung und Standby](#4-stromversorgung-und-standby)
  - [5. Thermomanagement und Lüfter](#5-thermomanagement-und-lüfter)
  - [6. Videoeinstellungen](#6-videoeinstellungen)
  - [7. Autofokus](#7-autofokus)
  - [8. HDMI-Ausgabe](#8-hdmi-ausgabe)
- [Teil III — Objektive](#teil-iii--objektive)
  - [9. Samyang AF 35-150mm F2-2.8](#9-samyang-af-35-150mm-f2-28)
  - [10. Lumix S 18-40mm F4.5-6.3 (Kit)](#10-lumix-s-18-40mm-f45-63-kit)
- [Teil IV — Streaming-Setup](#teil-iv--streaming-setup)
  - [11. OBS Studio und Encoder](#11-obs-studio-und-encoder)
  - [12. Blackmagic DeckLink Capture](#12-blackmagic-decklink-capture)
  - [13. Szenen-Konfiguration (Hosanna)](#13-szenen-konfiguration-hosanna)
  - [14. Netzwerk und NDI](#14-netzwerk-und-ndi)
  - [15. Best Practices Langzeit-Streaming](#15-best-practices-langzeit-streaming)
- [Teil V — Erfahrungsberichte und Lehren](#teil-v--erfahrungsberichte-und-lehren)
  - [16. Vorfall: Kamera ging im Stream aus (Mai 2026)](#16-vorfall-kamera-ging-im-stream-aus-mai-2026)
- [Anhang](#anhang)
  - [A. Dokumentationsstruktur im Repo](#a-dokumentationsstruktur-im-repo)
  - [B. Glossar](#b-glossar)

---

## Über dieses Handbuch

Das Repo ist als **lebendes Handbuch** gedacht: jede Erkenntnis aus dem Praxis-Einsatz (vor allem aus den Hosanna-Gottesdienst-Streams) fließt zurück in die entsprechenden Kapitel. Wenn ein Begriff unklar ist, im [Glossar](#b-glossar) nachschlagen oder die Erklärung im jeweiligen Kapitel suchen — Fachbegriffe werden bei der ersten Verwendung im Klartext erklärt.

**Wie lesen?**
- **Erstes Mal:** Teil I → II in Reihenfolge, dann III–IV nach Bedarf.
- **Schnell etwas nachschlagen:** über das Inhaltsverzeichnis direkt zum Kapitel springen.
- **Vor einem Stream:** [Schnellstart](#schnellstart) öffnen.

Alle Angaben beziehen sich auf die **EU-Firmware 2.7** der S5IIX, sofern nicht anders vermerkt.

---

## Schnellstart

Wenn der Gottesdienst in einer Stunde anfängt, hier entlang:

- **[Schnellstart-Anleitung Sonntagsgottesdienst](docs/QUICK-START.md)** — 60-Min-Countdown, Aufbau-Checkliste, Notfall-Karte für den Streaming-PC

---

## Teil I — Grundlagen

### 1. Mein Setup

| Komponente | Detail |
|---|---|
| Kamera (neu) | Panasonic Lumix DC-S5IIX (Gehäuse-FW 2.6, Dez. 2025) — SN: WJ5DC001118 |
| Objektiv-Firmware | Samyang AF 35-150mm F2-2.8 — FW 3.6 |
| Kamera (aktuell, parallel) | Panasonic AW-HE40HW PTZ (SDI → DeckLink) |
| Capture Card | Blackmagic DeckLink Mini Recorder 4K (SDI für PTZ, HDMI für S5IIX) |
| Software | OBS Studio 32.1.2 (Windows 11 Pro) |
| Encoder | NVIDIA NVENC AV1 (RTX 4060, 10 Mbps, p6) |
| Audio | Focusrite Scarlett 2i2 USB (WASAPI, 48 kHz, +60 ms Offset) |
| NDI | DistroAV v6.2.1 — Beamer-PC (SongBeamer) → OBS |
| Objektiv 1 | Samyang AF 35-150mm F2-2.8 (L-Mount) |
| Objektiv 2 | Panasonic Lumix S 18-40mm F4.5-6.3 (Kit) |
| Speicherkarte | V60 SDXC (Stand 2026-05-21) |
| Netzwerk | Gigabit LAN, Vodafone Cable (1 Gbit Down / 50 Mbit Up) |
| Einsatz | Kirchen-Gottesdienste Hosanna (1–3 h, variable Beleuchtung) |

### 2. Region und Systemfrequenz

EU-Modell (Deutschland). Wichtigste Konsequenz: **Systemfrequenz immer 50,00 Hz (PAL)**, weil das EU-Stromnetz mit 50 Hz läuft. Falsch gewählte Frequenzen führen zu sichtbarem Flicker bei Kunstlicht.

Verfügbare Bildraten in PAL: 25p, 50p, 100p. Empfehlung für Streaming: **25p**.

→ Details und Begründung im Kapitel [6. Videoeinstellungen](#6-videoeinstellungen).

### 3. Firmware-Stand

Die EU-Firmware unterscheidet sich von japanischen/US-Versionen — manche Funktionen sind eingeschränkt oder entfernt (z. B. eingebautes RTMP-Streaming seit FW 2.2). Vor jedem Firmware-Update prüfen, ob etwas Genutztes wegfällt.

- **[Firmware-Changelog & EU-Einschränkungen](docs/camera/firmware-changelog.md)** — Versionshistorie v1.0–v3.7, regionale Unterschiede, Verifikations-Checkliste

---

## Teil II — Die Kamera einrichten

Die Reihenfolge in diesem Teil ist bewusst gewählt: erst dafür sorgen, dass die Kamera **stabil läuft** (Strom, Wärme), dann die Bild-Einstellungen, am Ende die Schnittstelle zur Außenwelt (HDMI).

### 4. Stromversorgung und Standby

Die wichtigste Lektion aus dem Live-Einsatz: **Standby-Modi explizit ausschalten**. Die Kamera kann sonst mitten im Stream abschalten — ist genau das im Mai 2026 passiert (siehe [Kapitel 16](#16-vorfall-kamera-ging-im-stream-aus-mai-2026)).

- **[Stromversorgung & Standby-Vermeidung](docs/camera/power-management.md)** — USB-PD-Anforderungen, Sleep-Modi deaktivieren, Akku als USV, Vor-Stream-Checkliste

### 5. Thermomanagement und Lüfter

Bei langen Aufnahmen wird die S5IIX warm. Sie hat einen aktiven Lüfter — der sollte für lange Streams auf einen passenden Modus stehen.

- **[Thermomanagement & Lüfter](docs/camera/thermal-management.md)** — Lüfter-Modi (AUTO1/2, FAST, SLOW, OFF), Temperaturmanagement-Einstellung, Wärme reduzieren

### 6. Videoeinstellungen

Hier wird festgelegt, welches Bild die Kamera produziert: Auflösung, Bildrate, Verschlusszeit, Bildstil. Mit ausführlichem Glossar zu Begriffen wie *Open Gate*, *LongGOP*, *Bitrate* etc.

- **[Videoeinstellungen](docs/camera/video-settings.md)** — Systemfrequenz, Aufnahmeformate (MOV/MP4), Bildrate, 180°-Shutter-Regel, Bildstil, vollständige Format-Matrix, Stresstest-Modi

### 7. Autofokus

Der Autofokus muss in der Kirche **ruhig** arbeiten (kein Pumpen/Hunting), darf aber nicht aussteigen, wenn der Pastor sich bewegt.

- **[Autofokus-Einstellungen](docs/camera/af-settings.md)** — AF-Modi für Kirche, Gesichts-/Augenerkennung, Hunting-Vermeidung, Beispielszenarien

### 8. HDMI-Ausgabe

Das Bild geht über HDMI in die DeckLink-Capture-Karte. „Clean HDMI" heißt: ohne Menü-Overlays.

- **[HDMI-Output](docs/camera/hdmi-output.md)** — Clean HDMI, 4K vs 1080p, Farbtiefe, Kabel-Empfehlungen

---

## Teil III — Objektive

### 9. Samyang AF 35-150mm F2-2.8

Das Hauptobjektiv für Hosanna. Lichtstark, deckt von leichtem Weitwinkel bis Tele alles ab.

- **[Samyang AF 35-150mm F2-2.8](docs/lenses/samyang-35-150.md)** — Hauptobjektiv, AF-Verhalten, optimale Einstellungen, bekannte Einschränkungen

### 10. Lumix S 18-40mm F4.5-6.3 (Kit)

Das Kit-Objektiv. Lichtschwach — nur für Weitwinkel-Backup geeignet.

- **[Panasonic Lumix S 18-40mm F4.5-6.3](docs/lenses/lumix-18-40.md)** — Kit-Objektiv, Lichtschwäche-Analyse, Einsatzgrenzen

---

## Teil IV — Streaming-Setup

### 11. OBS Studio und Encoder

Wie das Bild aus der Kamera am Ende bei YouTube/Facebook landet.

- **[Encoder-Einstellungen (NVENC AV1)](docs/obs/encoder-settings.md)** — AV1 10 Mbps p6, Szenen-Konfiguration, Bandbreiten-Planung

### 12. Blackmagic DeckLink Capture

Die Hardware-Brücke zwischen Kamera-HDMI und PC.

- **[Blackmagic DeckLink Setup](docs/obs/blackmagic-setup.md)** — Desktop Video Konfiguration, SDI/HDMI, OBS-Integration

### 13. Szenen-Konfiguration (Hosanna)

Wie die Szenen in OBS für den Gottesdienst aufgebaut sind.

- **[Szenen-Konfiguration (Hosanna)](docs/obs/scene-config.md)** — Signal-Flow, Scene Collection, NDI-Workflow, S5IIX-Integration

### 14. Netzwerk und NDI

NDI bringt das SongBeamer-Bild vom Beamer-PC in OBS, ohne zweites HDMI-Kabel quer durch den Saal.

- **[Netzwerk-Architektur & NDI](docs/streaming/network-config.md)** — LAN-Setup, NDI-Praxis, Signal-Formate, Multi-Cam-Planung

### 15. Best Practices Langzeit-Streaming

Was sich in den vergangenen Streams bewährt hat — und was nicht.

- **[Best Practices Langzeit-Streaming](docs/streaming/best-practices.md)** — Vor-Ort-Checkliste, Belichtungsstrategie, Dual Native ISO, Audio, Wartung

---

## Teil V — Erfahrungsberichte und Lehren

Echte Vorfälle aus dem Live-Einsatz. Werden hier dokumentiert, damit der gleiche Fehler nicht zweimal passiert.

### 16. Vorfall: Kamera ging im Stream aus (Mai 2026)

Der Ruhemodus-Werks-Default (5 Min) hat die S5IIX trotz aktiver HDMI-Ausgabe mitten im Gottesdienst abgeschaltet.

- **[Vorfall-Bericht](docs/camera/standby-incident-2026-05.md)** — Diagnose Ruhemodus-Default, Vorher/Nachher-Konfiguration, abgeleitete Standard-Einstellung

---

## Anhang

### A. Dokumentationsstruktur im Repo

```
docs/
├── camera/
│   ├── firmware-changelog.md          # Kapitel 3
│   ├── power-management.md            # Kapitel 4
│   ├── thermal-management.md          # Kapitel 5
│   ├── video-settings.md              # Kapitel 6
│   ├── af-settings.md                 # Kapitel 7
│   ├── hdmi-output.md                 # Kapitel 8
│   └── standby-incident-2026-05.md    # Kapitel 16
├── lenses/
│   ├── samyang-35-150.md              # Kapitel 9
│   └── lumix-18-40.md                 # Kapitel 10
├── obs/
│   ├── encoder-settings.md            # Kapitel 11
│   ├── blackmagic-setup.md            # Kapitel 12
│   └── scene-config.md                # Kapitel 13
├── streaming/
│   ├── network-config.md              # Kapitel 14
│   └── best-practices.md              # Kapitel 15
└── QUICK-START.md                     # Schnellstart
```

### B. Glossar

Häufig auftauchende Begriffe in einer Zeile. Ausführlichere Erklärungen jeweils im zugehörigen Kapitel.

| Begriff | Bedeutung |
|---|---|
| **PAL / 50 Hz** | EU-Videostandard, 25 Bilder pro Sekunde, passt zur 50-Hz-Stromnetzfrequenz. |
| **NTSC / 60 Hz** | Amerikanischer Videostandard, 30 Bilder pro Sekunde — in EU vermeiden. |
| **Bildrate / fps / `25p`** | Bilder pro Sekunde. `p` = progressiv (jedes Bild komplett). |
| **Verschlusszeit / Shutter** | Wie lange jedes Einzelbild belichtet wird (z. B. 1/50 Sekunde). |
| **180°-Regel** | Faustregel: Verschlusszeit = doppelte Bildrate (bei 25p → 1/50 s). Sorgt für natürliche Bewegungsunschärfe. |
| **Auflösung** | Bildpunkte breit × hoch. FHD = 1920×1080, 4K UHD ≈ 3840×2160, 6K ≈ 5952 breit. |
| **Open Gate** | Aufnahme über die komplette Sensorfläche, ohne Beschnitt. |
| **Full-frame / APS-C** | Genutzte Sensorfläche. Full-frame = ganzer Sensor; APS-C = mittlerer Ausschnitt (~1,5× Tele-Effekt). |
| **Codec** | Kompressionsverfahren. Für uns relevant: **LongGOP** (sparsam) und **ALL-Intra** (riesige Dateien). |
| **Bitrate (Mbps)** | Datenmenge pro Sekunde. Mehr = bessere Qualität, mehr Speicherbedarf. |
| **V60 / V90 (SD-Karte)** | Mindest-Schreibgeschwindigkeitsklasse einer SD-Karte. V60 = mind. 60 MB/s. |
| **HDMI Clean Output** | HDMI-Ausgabe ohne Kamera-Menü-Overlays — Pflicht für Streaming. |
| **NDI** | Network Device Interface — Video über LAN ohne Kabel. |
| **Capture Card** | Hardware, die das HDMI-/SDI-Signal in den PC bringt (hier: Blackmagic DeckLink). |
| **NVENC AV1** | Hardware-Encoder der NVIDIA-Grafikkarte, kodiert das Stream-Video effizient. |
