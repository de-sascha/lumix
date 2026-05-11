# OBS Studio Encoder-Einstellungen — NVENC Optimierung

## Hardware-Überblick (Hosanna Livestream PC)

| Komponente | Detail |
|---|---|
| PC | AMD Ryzen 5 7600X, 32 GB DDR5, Windows 11 Pro 25H2 |
| GPU | NVIDIA GeForce RTX 4060 (8 GB VRAM, NVENC AV1/HEVC/H.264) |
| Capture | Blackmagic DeckLink Mini Recorder 4K (SDI für PTZ), Mirabox USB (Fallback) |
| NDI | DistroAV v6.2.1 (Beamer PC → Presentation) |
| Audio | Focusrite Scarlett 2i2 USB (WASAPI, 48 kHz) |
| Encoder | NVIDIA NVENC AV1 (primary), HEVC (recording) |
| Output | YouTube Live (RTMPS) |
| Upload | 50 Mbit/s (Vodafone Cable) |
| OBS Version | 32.1.2 |

## Aktive Streaming-Einstellungen (Hosanna Praxis) `[VERIFIZIERT]`

### NVENC AV1 — 1080p30 (im Einsatz)

**OBS > Einstellungen > Ausgabe > Streaming (Simple Mode)**

| Parameter | Wert | Begründung |
|---|---|---|
| Encoder | **NVIDIA NVENC AV1** | Neueste Generation, beste Effizienz bei gleicher Bitrate |
| Bitrate | **10.000 Kbps** | Hohe Qualität für 1080p30, innerhalb Upload-Budget |
| Preset | **p6 (Slow)** | Maximale Qualität bei gegebener Bitrate |
| Color Format | NV12 | Standard für Streaming |
| Color Range | Full | Volles Spektrum |
| Color Space | sRGB | Web-kompatibel |

### Video-Einstellungen

| Parameter | Wert |
|---|---|
| Base (Canvas) Resolution | 1920×1080 |
| Output (Scaled) Resolution | 1920×1080 |
| Downscale Filter | Lanczos |
| FPS | **30** |

> **Hinweis PAL/NTSC:** OBS läuft mit 30fps obwohl die S5IIX im PAL-Modus (25p/50p) arbeitet. Die DeckLink und OBS übernehmen die Frame-Konvertierung. Bei der PTZ-Kamera (AW-HE40HW) liefert diese 59.94i/29.97p via SDI (NTSC-Gerät).

---

## Alternative Encoder-Optionen

### H.264 (Fallback / ältere GPUs)

| Parameter | Wert | Begründung |
|---|---|---|
| Encoder | NVIDIA NVENC H.264 (new) | Breiteste Kompatibilität |
| Rate Control | CBR | Pflicht für die meisten Streaming-Plattformen |
| Bitrate | 8.000 - 12.000 Kbps | 8K für Sicherheit, 12K für max. Qualität |
| Keyframe Interval | 2 Sekunden | YouTube/Facebook Anforderung |
| Preset | Quality (P5) | Guter Kompromiss aus Qualität und Last |
| Profile | High | Beste Kompression bei H.264 |
| Look-ahead | ON | Verbessert Qualität bei statischen Szenen |
| B-Frames | 2 | Standard für Streaming |

### HEVC / 4K (nur mit ausreichend Upload)

| Parameter | Wert |
|---|---|
| Encoder | NVIDIA NVENC HEVC (H.265) |
| Rate Control | CBR |
| Bitrate | 20.000 - 35.000 Kbps |
| Keyframe Interval | 2 Sekunden |
| Preset | Quality (P5) |
| Profile | Main (HEVC) |

**Hinweis:** 4K-Streaming erfordert deutlich mehr Upload-Bandbreite. Bei 35 Mbit Stream + Overhead nutzt man bereits 70-80% der 50 Mbit Upload-Leitung. Empfehlung: **1080p streamen, 4K-Input für Crop-Flexibilität nutzen.**

### AV1 vs H.264 — Warum AV1?

| Kriterium | AV1 | H.264 |
|---|---|---|
| Qualität bei 10 Mbps | Deutlich besser | Gut |
| GPU-Anforderung | RTX 4000+ | Jede NVENC-GPU |
| YouTube-Support | Ja (bevorzugt) | Ja |
| CPU-Last | ~0% (Hardware) | ~0% (Hardware) |
| Kompatibilität | Neuere Player | Universell |

AV1 liefert bei gleicher Bitrate ca. 30% bessere Bildqualität als H.264.

## OBS Canvas-Einstellungen

**OBS > Einstellungen > Video**

| Parameter | Wert (bei 4K-Input) | Wert (bei 1080p-Input, aktuell) |
|---|---|---|
| Base Resolution | 3840×2160 | 1920×1080 |
| Output Resolution | 1920×1080 | 1920×1080 |
| Downscale Filter | Lanczos (Schärfer) | Lanczos |
| FPS | 30 | 30 |

## Quellen in OBS (Hosanna Setup) `[VERIFIZIERT]`

### Source: "Panasonic CAM" (PTZ Kamera via DeckLink)

| Parameter | Wert |
|---|---|
| Type | Blackmagic Device |
| Device | DeckLink Mini Recorder 4K |
| Video Connection | SDI |
| Audio Connection | Embedded SDI |
| Mode | Auto Detect |
| Pixel Format | 8-bit YUV |
| Color Space | BT.709 |
| Color Range | Full |
| Buffering | Enabled |

### Source: "Beamer NDI Texte" (Primär-Präsentation)

| Parameter | Wert |
|---|---|
| Type | NDI Source (DistroAV) |
| NDI Source Name | BEAMERPC (SongBeamer) |
| Bandwidth | Highest |
| Latency | Low |
| Hardware Acceleration | Enabled (RTX 4060) |
| Sync Mode | NDI Timestamp |
| YUV Range | Full |
| YUV Colorspace | BT.709 |

### Source: "Songbeamer klassisch (kein NDI)" (Fallback)

| Parameter | Wert |
|---|---|
| Type | Video Capture Device (DirectShow) |
| Device | MiraBox Video Capture |
| Resolution | Default (auto) |
| Color Space | BT.601 |
| Note | Nur wenn Mirabox physisch via USB 3.0 angeschlossen |

### Source: "Beamer Screen" (Vollbild NDI für Videos)

| Parameter | Wert |
|---|---|
| Type | NDI Source (DistroAV) |
| NDI Source Name | BEAMERPC (SongBeamer) |
| Purpose | Vollbild inkl. Video-Playback |

### Wichtig: Desktop Video muss installiert sein

OBS erkennt die DeckLink nur, wenn die **Blackmagic Desktop Video Software** installiert und konfiguriert ist.

## Bandbreiten-Planung

| Stream-Profil | Bitrate | Upload-Auslastung (50 Mbit) | Headroom |
|---|---|---|---|
| **1080p30 AV1 (aktuell)** | **10 Mbps** | **20%** | **80% — ideal** |
| 1080p30 H.264 Standard | 8 Mbps | 16% | 84% — sehr sicher |
| 1080p30 H.264 High Quality | 12 Mbps | 24% | 76% — sicher |
| 4K30 HEVC | 20-35 Mbps | 40-70% | 30-60% — riskant bei Cable |

### Empfehlung: **10 Mbps AV1 (1080p30)**

AV1 bei 10 Mbps liefert vergleichbare Qualität zu H.264 bei 15+ Mbps. Kabel-Internet hat variable Upload-Performance — Headroom von >50% ist empfehlenswert, um Dropped Frames bei Netzwerk-Schwankungen zu vermeiden.

## Lokale Aufnahme (Backup) `[VERIFIZIERT]`

**Parallel zum Stream eine lokale Aufnahme in OBS:**

| Parameter | Wert |
|---|---|
| Encoder | **NVENC HEVC** |
| Quality | Small File Size |
| Recording Format | **Fragmented MP4** |
| Output | C:/Users/Hosanna Livestream/Videos |

> **Hinweis:** Fragmented MP4 (statt MKV) wird verwendet — bei Absturz bleibt die Datei intakt, da Header progressiv geschrieben werden. Kein Remux nötig.

## Szenen-Konfiguration: "Hosanna Gottesdienst" `[VERIFIZIERT]`

### Szenen-Gruppen (Scene Collection)

| Gruppe | Szene | Zweck |
|---|---|---|
| **ANFANG/ENDE** | Livestream Start Video | Countdown-Loop + Musik vor dem Gottesdienst |
| | Livestream Ende Video | QR-Spenden, Abschied, Outro-Musik |
| **LOBPREIS** | Lobpreis - Kamera Vollbild | Kamera-Vollbild bei Worship |
| | Lobpreis - unten dunkel überblendet | Kamera mit dunklem Farbverlauf unten |
| | Lobpreis - Glaubensbekenntnis | Kamera + NDI-Text-Overlay |
| | Lobpreis - Jesus Schild | Kamera + Bild-Overlay |
| | Lobpreis - Videos zeigen | Worship-Hintergrundvideos |
| **PREDIGT** | Predigt - Kamera Vollbild | Kamera-Vollbild bei Predigt |
| | Predigt - Power Point / Folien | NDI-Präsentation Vollbild (Slides) |
| | Lobpreis - Vater Unser | Kamera + Text-Overlay |
| **BIBEL** | Bibel Text unten | Kamera + Bibeltext am unteren Rand |
| | Bibel als Text - Vollbild, schwarzer Hintergrund | Bibeltext auf Schwarz |
| | Bibel als Bild - Vollbild, dunkelviolett | Bibel-Bild (dunkelviolett) |
| | Bibel als Text - Vollbild transparent | Bibeltext transparent |
| | Bibel als Text - Kamera klein unten rechts | Bibeltext + kleine Kamera |
| | Bibel als Text - links oben grau hinterlegt | Bibeltext links oben |
| **ANKÜNDIGUNGEN** | Ankündigungen - Vollbild | NDI-Präsentation Vollbild |
| **EXTRAS** | Beamer Videos zeigen | Mirabox-Passthrough (USB-Fallback) |

### Studio Mode

| Einstellung | Wert |
|---|---|
| Preview/Program Mode | Enabled |
| Transition | Swipe |
| Hotkey Transition | Ctrl+Shift+Enter / Numpad + |
| Confirm on Exit | Enabled |
| Warn before start | Enabled |

### NDI Output (für andere Geräte im Netzwerk)

OBS sendet das Program-Signal als NDI-Output ins LAN:

| Einstellung | Wert |
|---|---|
| Main Output | Enabled |
| Output Name | "HDMI Kamera" |
| Tally (Program/Preview) | Enabled |

## Audio-Einstellungen (Hosanna Setup) `[VERIFIZIERT]`

### Audio-Interface: Focusrite Scarlett 2i2

| Parameter | Wert |
|---|---|
| OBS Source Name | "Mischpult" |
| Type | WASAPI Audio Input Capture |
| Device | Microphone (Scarlett 2i2 USB) |
| Sample Rate | 48 kHz |
| Channels | Stereo |
| **Sync Offset** | **+60 ms** (kompensiert Video-Processing-Delay) |
| Default State | Muted (manuell unmuten vor Gottesdienst!) |
| Volume Lock | Yes (verhindert versehentliche Änderung) |

### Audio-Filter-Chain

| Filter | Einstellungen |
|---|---|
| Limiter | Threshold: -1.5 dB, Release: 68 ms |

### Monitoring

| Parameter | Wert |
|---|---|
| Monitoring Device | Realtek Onboard Audio (Lautsprecher) |
| Desktop Audio | Nicht konfiguriert |
| Audio Bitrate (Stream) | 192 kbps AAC |

### Audio-Workflow (Prinzip)

```
┌────────────┐    XLR    ┌──────────────────┐   USB    ┌─────────┐
│ Kirchen-   │──────────│ Focusrite        │────────│ OBS PC  │
│ Mischpult  │          │ Scarlett 2i2     │         │         │
└────────────┘          └──────────────────┘         └─────────┘
```

> **WICHTIG:** Audio kommt NICHT von der Kamera! Kamera-Audio ist für Streaming ungeeignet (Raumhall, Lüftergeräusch, zu weit vom Sprecher entfernt).

## Streaming-Plattform-Konfiguration

### YouTube Live `[VERIFIZIERT]`

**OBS > Einstellungen > Stream**

| Parameter | Wert |
|---|---|
| Service | YouTube / YouTube Gaming |
| Protocol | RTMPS |
| Server | rtmp://a.rtmp.youtube.com/live2 |
| Stream Key | Aus YouTube Studio (beim Admin erfragen) |

## Performance-Monitoring

| Indikator | Zielwert | Bei Überschreitung |
|---|---|---|
| Encoding (untere Leiste) | < 5% | Preset reduzieren (p6 → p5) |
| Rendering Lag | 0% | GPU entlasten, Preview-Qualität senken |
| Dropped Frames | 0 | Netzwerk prüfen, Bitrate senken |
| CPU Usage | < 15% | Normal bei NVENC (GPU übernimmt Encoding) |

## Troubleshooting

| Problem | Lösung |
|---|---|
| Dropped Frames (Encoding) | GPU überlastet → andere Apps schließen, Preview reduzieren |
| Dropped Frames (Network) | Bitrate reduzieren, LAN-Kabel prüfen |
| "Encoding overloaded" | GPU unter Last → andere GPU-intensive Apps schließen |
| Kein DeckLink-Signal in OBS | Desktop Video Setup → Input-Format prüfen |
| Audio-Drift | Sync Offset anpassen (aktuell +60 ms) |
| Schwarzes Bild | Kamera-HDMI/SDI-Output prüfen, Info Display OFF |
| Farben falsch | Photo Style auf Standard/Natural, kein V-Log |
| Mirabox "GetDevice failed" | USB-Gerät vor OBS-Start anschließen, ggf. Reboot |
| NDI Source nicht gefunden | SongBeamer auf Beamer PC läuft? LAN-Verbindung prüfen |
| Stream Key expired | Neuen Key aus YouTube Studio holen |
| Audio monitoring error (80070490) | Unkritisch — betrifft nur Vorschau, nicht den Stream |
