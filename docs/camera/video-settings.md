# Videoeinstellungen — Panasonic Lumix DC-S5IIX für Kirchenstreaming

## Systemfrequenz

**Setup-Menü > Sonstige > Systemfrequenz**

| Option | Verfügbare Bildraten | Empfehlung |
|---|---|---|
| **50,00 Hz (PAL)** | 25p, 50p, 100p | **Standard für EU/Deutschland** |
| 59,94 Hz (NTSC) | 23,98p, 29,97p, 47,95p, 59,94p, 119,88p | Nur wenn Streaming-Plattform NTSC bevorzugt |
| 24,00 Hz (CINEMA) | 24p, 48p | Kino-Look, nicht für Streaming empfohlen |

### Empfehlung: **50,00 Hz (PAL)**

Begründung:
- EU-Netzfrequenz = 50Hz → Vermeidung von Banding/Flicker bei Kunstlicht
- Shutter-Speed 1/50s harmoniert mit 50Hz Lichtfrequenz
- YouTube/Facebook verarbeiten PAL-Material problemlos

## Aufnahmeformat (für HDMI-Output)

Da die Kamera primär über HDMI an die DeckLink ausgibt, ist das interne Aufnahmeformat sekundär. Trotzdem die Empfehlung:

### Modus: Kreative Filme (Creative Video)

Kamera-Modusrad auf **M** (Videomodus) stellen.

### HDMI-Output-Konfiguration

**Videomenü > Bildformat > RAW-Datenausgabe über HDMI: OFF**

Für reines Streaming benötigen Sie kein RAW-Output. Standard-HDMI genügt.

## Empfohlene Video-Qualitätseinstellungen

### Für Streaming (HDMI-Output, keine interne Aufnahme)

| Parameter | Einstellung | Begründung |
|---|---|---|
| Bildgröße | FHD (1920×1080) oder 4K (3840×2160) | 4K für Crop-Möglichkeit in OBS |
| Bildrate | 25p (PAL) | Kirchliche Inhalte brauchen keine 50p |
| Codec | Irrelevant bei HDMI-only | Kein internes Recording |
| Farbtiefe HDMI | 4:2:2 10-Bit | DeckLink 4K unterstützt dies |

### Falls zusätzliche interne Backup-Aufnahme gewünscht

| Parameter | Einstellung | Begründung |
|---|---|---|
| Dateiformat | MP4 | Kompatibel, robuster bei Abbruch |
| Bildgröße | FHD (1920×1080) | Minimale Wärmeentwicklung |
| Codec | H.264/AVC 4:2:0 8-Bit | Geringste Last |
| Komprimierung | Long GOP | Geringere Datenrate |
| Bitrate | 20-28 Mbit | Ausreichend für FHD Backup |

## Bildrate & Shutter-Speed (180°-Regel)

| Systemfrequenz | Bildrate | Shutter-Speed | Anmerkung |
|---|---|---|---|
| 50 Hz (PAL) | 25p | **1/50s** | Standard — natürlicher Motion Blur |
| 50 Hz (PAL) | 50p | **1/100s** | Flüssiger, mehr Licht nötig |
| 59.94 Hz (NTSC) | 29.97p | **1/60s** | Falls NTSC gewählt |

### Wichtig: Shutter-Speed und Kunstlicht

In der EU mit 50Hz-Stromnetz:
- Shutter **1/50s** oder **1/100s** → kein Flicker
- Shutter 1/60s bei 50Hz-Licht → **Banding/Flicker-Gefahr!**
- Wenn NTSC (29.97p) gewählt: 1/60s KANN in EU-Kirchen flickern!

**→ Deshalb immer PAL (50Hz) in der EU verwenden.**

## Bildstil (Photo Style)

**Videomenü > Bildstil**

| Bildstil | Anwendung | Empfehlung für Streaming |
|---|---|---|
| **Standard** | Gut aussehendes Bild direkt aus der Kamera | **Empfohlen** |
| **Natural** | Etwas dezenter, weniger gesättigt | **Alternative** |
| Wie709 | Broadcast-Standard Rec.709 | Für professionelle Workflows |
| V-Log | Flach, für Nachbearbeitung | **NICHT für Live-Streaming** |

### Warum NICHT V-Log für Streaming?

- V-Log erfordert einen LUT in OBS → zusätzliche Komplexität
- Ohne LUT sieht das Bild flach und unattraktiv aus
- Mehr Arbeit ohne Nutzen im Live-Streaming-Kontext
- Standard/Natural sieht direkt auf dem Stream gut aus

## Aufnahmequalitäten-Übersicht (PAL, Full Frame)

### MP4-Format (Long GOP)

| Bildgröße | Bildrate | Codec | Bitrate |
|---|---|---|---|
| 4K 3840×2160 | 50p | 10-Bit HEVC 4:2:0 | 100 Mbit |
| 4K 3840×2160 | 25p | 10-Bit HEVC 4:2:0 | 72 Mbit |
| 4K 3840×2160 | 50p | 8-Bit AVC 4:2:0 | – |
| 4K 3840×2160 | 25p | 8-Bit AVC 4:2:0 | 100 Mbit |
| FHD 1920×1080 | 50p | 8-Bit AVC 4:2:0 | 28 Mbit |
| FHD 1920×1080 | 25p | 8-Bit AVC 4:2:0 | 20 Mbit |

### MOV-Format (Long GOP und All-Intra)

Höhere Qualitäten bis 6K verfügbar (nur im Modus Kreative Filme).

## Dauer-AF-Einstellung für Video

**Videomenü > Fokus > Dauer-AF**

| Modus | Verhalten | Empfehlung |
|---|---|---|
| **MODE 1** | AF nur während Videoaufnahme aktiv | **Empfohlen** — spart Energie |
| MODE 2 | AF auch in Filmpausen aktiv | Mehr Energieverbrauch |
| OFF | Kein AF während Video | Nur für manuellen Fokus |

## Zusammenfassung Kirchenstreaming-Setup

```
Systemfrequenz:        50,00 Hz (PAL)
Modus:                 Kreative Filme (M)
Bildgröße HDMI:        4K oder FHD (je nach Bedarf)
Bildrate:              25p
Shutter:               1/50s (fest)
Bildstil:              Standard oder Natural
Weißabgleich:          Manuell/Kelvin (3200-5000K messen!)
Dauer-AF:              MODE 1
Interne Aufnahme:      AUS (oder FHD 25p 8-Bit als Backup)
```
