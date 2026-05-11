# OBS Studio Encoder-Einstellungen — NVENC Optimierung

## Hardware-Überblick

| Komponente | Detail |
|---|---|
| Capture | Blackmagic DeckLink Mini Recorder 4K |
| Encoder | NVIDIA NVENC (Hardware-Encoder der GPU) |
| Output | YouTube Live / Facebook Live / Custom RTMP |
| Upload | 50 Mbit/s (Vodafone Cable) |

## Empfohlene Streaming-Einstellungen

### 1080p25 Stream (Standard-Empfehlung)

**OBS > Einstellungen > Ausgabe > Streaming**

| Parameter | Wert | Begründung |
|---|---|---|
| Encoder | NVIDIA NVENC H.264 (new) | Hardware-beschleunigt, geringe CPU-Last |
| Rate Control | CBR | Pflicht für die meisten Streaming-Plattformen |
| Bitrate | 8.000 - 12.000 Kbps | 8K für Bandbreiten-Sicherheit, 12K für maximale Qualität |
| Keyframe Interval | 2 Sekunden | YouTube/Facebook Anforderung |
| Preset | Quality (P5) | Guter Kompromiss aus Qualität und Last |
| Profile | High | Beste Kompression bei H.264 |
| Look-ahead | ON | Verbessert Qualität bei statischen Szenen |
| B-Frames | 2 | Standard für Streaming |

### 4K25 Stream (falls gewünscht)

| Parameter | Wert |
|---|---|
| Encoder | NVIDIA NVENC HEVC (H.265) |
| Rate Control | CBR |
| Bitrate | 20.000 - 35.000 Kbps |
| Keyframe Interval | 2 Sekunden |
| Preset | Quality (P5) |
| Profile | Main (HEVC) |

**Hinweis:** 4K-Streaming erfordert deutlich mehr Upload-Bandbreite. Bei 35 Mbit Stream + Overhead nutzt man bereits 70-80% der 50 Mbit Upload-Leitung. Empfehlung: **1080p25 streamen, 4K-Input für Crop-Flexibilität nutzen.**

## OBS Canvas-Einstellungen

**OBS > Einstellungen > Video**

| Parameter | Wert (bei 4K-Input) | Wert (bei 1080p-Input) |
|---|---|---|
| Base Resolution | 3840×2160 | 1920×1080 |
| Output Resolution | 1920×1080 | 1920×1080 |
| Downscale Filter | Lanczos (Schärfer) | — |
| FPS | 25 (PAL) | 25 (PAL) |

## DeckLink als Quelle in OBS

### Quelle hinzufügen

1. Szene erstellen (z.B. "Kamera Hauptbild")
2. **+** > **Blackmagic Device** (oder "Decklink" je nach OBS-Version)
3. Device: **DeckLink Mini Recorder 4K**
4. Video Mode: **Auto** (oder manuell: 2160p25 / 1080p25)
5. Audio: **Embedded Audio (HDMI)**

### Wichtig: Desktop Video muss installiert sein

OBS erkennt die DeckLink nur, wenn die **Blackmagic Desktop Video Software** installiert und konfiguriert ist.

## Bandbreiten-Planung

| Stream-Profil | Bitrate | Upload-Auslastung (50 Mbit) | Headroom |
|---|---|---|---|
| 1080p25 Standard | 8 Mbps | 16% | 84% — sehr sicher |
| 1080p25 High Quality | 12 Mbps | 24% | 76% — sicher |
| 4K25 Standard | 20 Mbps | 40% | 60% — OK |
| 4K25 High Quality | 35 Mbps | 70% | 30% — riskant bei Cable |

### Empfehlung: **8-12 Mbps (1080p25)**

Kabel-Internet hat variable Upload-Performance. Headroom von >50% ist empfehlenswert, um Dropped Frames bei Netzwerk-Schwankungen zu vermeiden.

## Lokale Aufnahme (Backup)

**Parallel zum Stream eine lokale Aufnahme in OBS:**

| Parameter | Wert |
|---|---|
| Recording Format | MKV (remux zu MP4 nach Ende) |
| Encoder | NVENC H.264 (separater Encoder-Instance) |
| Rate Control | CRF |
| CRF Value | 18-20 |
| Preset | Quality (P5) |

MKV ist robuster als MP4 — bei Absturz bleibt die Datei intakt. Nach dem Stream: OBS > Datei > Aufnahmen remuxen > MKV → MP4.

## Szenen-Empfehlung für Kirchengottesdienst

| Szene | Beschreibung | Besonderheit |
|---|---|---|
| **Kamera Vollbild** | Kompletter 4K-Input | Standard-Szene |
| **Kamera Crop Prediger** | 200% Zoom auf Mitte | Für Predigt-Closeup |
| **Kamera + Lower Third** | Mit Texteinblendung | Für Lied-Titel, Ankündigungen |
| **Standbild** | Logo / Willkommen-Grafik | Vor/nach dem Gottesdienst |
| **Bildschirm** | Desktop-Capture | Für Präsentationen/Liedtexte |

### Crop/Zoom in OBS (bei 4K-Input)

1. Rechtsklick auf Quelle > **Transform** > **Edit Transform**
2. Crop einstellen (z.B. 960px oben/unten, 960px links/rechts = 2× Zoom)
3. Oder: Quelle vergrößern und Position anpassen
4. Szenen-Übergang: Smooth (Cut oder Fade 300ms)

## Audio-Einstellungen

Da Audio typischerweise NICHT von der Kamera kommt (externes Mischpult), sondern von einem separaten Audio-Interface:

| Parameter | Empfehlung |
|---|---|
| Audio-Quelle | Separates USB-Audio-Interface oder DeckLink-Embedded |
| Sample Rate | 48 kHz |
| Audio Bitrate | 192 kbps AAC |
| Channels | Stereo |

Falls Audio vom Kirchen-Mischpult direkt in die DeckLink eingespeist wird (über HDMI-Audio-Embedder): In OBS die DeckLink-Audio-Quelle verwenden.

## Streaming-Plattform-Konfiguration

### YouTube Live

**OBS > Einstellungen > Stream**

| Parameter | Wert |
|---|---|
| Service | YouTube - RTMPS |
| Server | Primary YouTube ingest server |
| Stream Key | Aus YouTube Studio kopieren |

### Custom RTMP (für eigene Website)

| Parameter | Wert |
|---|---|
| Service | Custom |
| Server | rtmp://your-server/live |
| Stream Key | Individuell |

## Troubleshooting

| Problem | Lösung |
|---|---|
| Dropped Frames (Encoding) | GPU überlastet → Preset von P7 auf P5 reduzieren |
| Dropped Frames (Network) | Bitrate reduzieren, Kabel-Verbindung statt WLAN prüfen |
| Kein DeckLink-Signal in OBS | Desktop Video Setup → Input auf HDMI umschalten |
| Audio-Drift | Sample Rate in OBS = Desktop Video = 48 kHz angleichen |
| Schwarzes Bild | Kamera-HDMI-Output prüfen, Info Display OFF |
| Farben falsch | Photo Style auf Standard/Natural, kein V-Log |
