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

### MOV-Format — Vollständige Liste (PAL 50,00 Hz, FW 2.7)

Verifiziert am 2026-05-21 durch Foto-Inspektion aller 6 Menüseiten am Gerät.
Listenansicht der Aufnahmequalität, sortiert nach Auflösungsklasse.

#### Seite 1/6 — Open Gate / 6K / 5.9K (Full-frame, höchste Auflösungen)

| Auflösung | Seitenverh. | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|---|
| 5952×3968 | 3:2 (Open Gate) | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 5952×3136 | 17:9 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 5888×3312 | 16:9 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 5888×3312 | 16:9 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps (zweite Variante) |

#### Seite 2/6 — APS-C 3.3K (Open Gate 4:3) und C4K-Übergang

| Auflösung | Seitenverh. | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|---|
| 3328×2496 | 4:3 (Open Gate) | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 50p | 4:2:2 10-Bit ALL-Intra | 600 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 25p | 4:2:2 10-Bit ALL-Intra | 400 Mbps |

#### Seite 3/6 — C4K (4096×2160, Cinema 4K, 17:9)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 4096×2160 | Full-frame | 50p | 4:2:2 10-Bit LongGOP | 200 Mbps |
| 4096×2160 | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 4096×2160 | Full-frame | 50p | 4:2:0 10-Bit LongGOP | – |
| 4096×2160 | APS-C | 50p | 4:2:2 10-Bit ALL-Intra | 600 Mbps |
| 4096×2160 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 4096×2160 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |
| 4096×2160 | Full-frame | 25p | 4:2:2 10-Bit ALL-Intra | 400 Mbps |

#### Seite 4/6 — 4K UHD (3840×2160, 16:9)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 3840×2160 | APS-C | 50p | 4:2:2 10-Bit ALL-Intra | 600 Mbps |
| 3840×2160 | APS-C | 50p | 4:2:2 10-Bit LongGOP | 200 Mbps |
| 3840×2160 | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 3840×2160 | Full-frame | 25p | 4:2:2 10-Bit ALL-Intra | 400 Mbps |
| 3840×2160 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 3840×2160 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |

#### Seite 5/6 — FHD 100p (High Frame Rate)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 1920×1080 | Full-frame | 100p | 4:2:2 10-Bit ALL-Intra | 400 Mbps |
| 1920×1080 | Full-frame | 100p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 1920×1080 | Full-frame | 100p | 4:2:0 10-Bit LongGOP | 150 Mbps |
| 1920×1080 | Full-frame | 50p | 4:2:2 10-Bit ALL-Intra | 200 Mbps |
| 1920×1080 | Full-frame | 50p | 4:2:2 10-Bit LongGOP | 100 Mbps |
| 1920×1080 | Full-frame | 50p | 4:2:0 10-Bit LongGOP | 100 Mbps |

#### Seite 6/6 — FHD 25p

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 1920×1080 | Full-frame | 25p | 4:2:2 10-Bit ALL-Intra | 200 Mbps |
| 1920×1080 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 100 Mbps |
| 1920×1080 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 100 Mbps |

### Worst-Case-Modi für Hitze-Stresstest (nur SD-Recording)

Sortiert nach erwarteter thermischer Last:

| Rang | Modus | Last-Profil | SD-Karte | ~Dauer 256 GB |
|---|---|---|---|---|
| 1 | 3.3K 4:3 50p ALL-Intra 600 Mbps (APS-C Open Gate) | Sensor + Encoder + Karte (Maximum) | V90 zwingend | ~57 Min |
| 2 | 4K UHD 50p ALL-Intra 600 Mbps (APS-C) | Encoder + Karte am Limit | V90 zwingend | ~57 Min |
| 3 | C4K 50p ALL-Intra 600 Mbps (APS-C) | Encoder + Karte am Limit | V90 zwingend | ~57 Min |
| 4 | C4K 25p ALL-Intra 400 Mbps (Full-frame) | Voller Sensor + Encoder | V90 zwingend | ~85 Min |
| 5 | 4K UHD 25p ALL-Intra 400 Mbps (Full-frame) | Voller Sensor + Encoder | V90 zwingend | ~85 Min |
| 6 | 5.9K 25p LongGOP 200 Mbps (Full-frame) | Voller Sensor-Readout | V60 reicht | ~170 Min |
| 7 | 6K Open Gate 25p LongGOP 200 Mbps (Full-frame 3:2) | Voller Sensor 3:2 (mehr Pixel als 5.9K) | V60 reicht | ~170 Min |

**Empfehlung Stresstest-Reihenfolge:**

1. **Sensor-Stress:** 6K Open Gate 25p LongGOP 200 Mbps Full-frame
   → längster Durchlauf (~2,8h), maximaler Sensor-Readout
2. **Encoder/Karten-Stress:** 4K UHD 50p ALL-Intra 600 Mbps APS-C
   → kürzerer Durchlauf (~1h), Bitrate am absoluten Limit
3. **Kombi-Worst-Case:** 3.3K 4:3 50p ALL-Intra 600 Mbps APS-C Open Gate
   → maximaler Sensor-Readout im APS-C-Bereich + maximale Bitrate

**SD-Karten-Anforderungen:**
- ≤ 200 Mbps → V60 ausreichend
- 400–600 Mbps ALL-Intra → **V90 zwingend** (sonst Aufnahme-Abbruch)
- Empfehlung: V90 in beiden Slots für Konsistenz

### Stresstest mit nur V60-Karte verfügbar

Wenn nur eine V60-Karte vorhanden ist, fallen alle ALL-Intra-Modi (400/600 Mbps) weg — die führen zum Aufnahme-Abbruch. Verbleibend: LongGOP-Modi ≤ 200 Mbps.

**Empfohlener Modus: 6K Open Gate 25p LongGOP 200 Mbps Full-frame**

| Parameter | Einstellung |
|---|---|
| Systemfrequenz | 50,00 Hz (PAL) |
| Aufnahmeformat | MOV |
| Aufnahmequalität | 5952×3968 3:2 Open Gate, 25p, 4:2:0 10-Bit LongGOP, 200 Mbps |
| Bildbereich | Full-frame |
| Erwartete Dauer auf 256 GB | ~170 Min (2,8 h) |

Begründung:
- 3:2 Open Gate liest mehr Sensorpixel als 5.9K 16:9 → maximaler Sensor-Stress, der mit V60 stabil bleibt
- Lange Laufzeit deckt realistischen Gottesdienst-Marathon ab
- Geht über bisherigen 4K-Test (2×3,5 h bestanden, 2026-05-21) hinaus, weil der Sensor mehr arbeiten muss

**Optionaler zweiter Durchlauf (Encoder-Last betonen):** 4K UHD 50p LongGOP 200 Mbps APS-C — doppelte Framerate, stärkerer Encoder-Anteil, ebenfalls V60-tauglich.

**Wichtige Begleit-Einstellungen für aussagekräftigen Stresstest:**
- Temperaturmanagement: HIGH (Setup > Monitor/Display)
- Lüfter Modus: AUTO2 (realistisch) oder SLOW (härter)
- Ruhemodus / Energie sparen: AUS (sonst vorzeitiger Abbruch — siehe `standby-incident-2026-05.md`)
- Bildstabilisator (IBIS): AUS
- LCD: eingeklappt (reduziert Kühlfläche bewusst)
- USB-PD-Netzteil + Akku drin (zusätzliche Wärme im Akkufach)
- Umgebung: 23–26 °C, kein direkter Luftzug

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
