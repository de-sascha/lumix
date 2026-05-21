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

#### Mini-Glossar — was bedeuten die Spalten?

Die Tabellen unten enthalten Fachbegriffe. Hier eine Übersetzung in normale Sprache:

- **Auflösung** (z. B. `5952×3968`) — wie viele Bildpunkte (Pixel) breit × hoch das Video hat. Mehr = schärfer, aber auch größere Dateien und mehr Wärme. FHD = 1920×1080 ("Full HD"), 4K UHD ≈ 3840×2160, 6K ≈ 5952 breit.
- **Seitenverhältnis** (z. B. `16:9`, `4:3`, `3:2`) — die Bildform. `16:9` ist das normale Fernseh-/YouTube-Format. `3:2` ist Foto-Format (etwas höher als 16:9). `4:3` ist quadratischer (alte Röhrenfernseher).
- **Open Gate** — die Kamera nutzt den **kompletten Sensor**, ohne oben/unten was abzuschneiden. Liefert das maximale Bild, das der Sensor liefern kann. Vorteil: man kann später frei reinzoomen/croppen. Nachteil: Sensor arbeitet am meisten → mehr Wärme.
- **Bildbereich** — wie viel des Sensors genutzt wird:
  - **Full-frame** = der ganze Sensor (volles Bild, mehr Lichtempfindlichkeit, weniger Schärfentiefe)
  - **APS-C** = nur der mittlere Ausschnitt des Sensors. Das wirkt wie ein Tele-Zoom (~1,5×), aber das Bild kommt von weniger Sensorfläche.
- **Bildrate** (z. B. `25p`, `50p`, `100p`) — wie viele Einzelbilder pro Sekunde aufgenommen werden. `25p` = 25 Bilder/Sekunde (PAL-Standard für TV in Europa). `50p` = doppelt so flüssig, aber doppelte Datenmenge. Das `p` heißt "progressiv" (jedes Bild komplett, im Gegensatz zu altem Halbbild-`i`).
- **Codec** — die Methode, wie das Video komprimiert wird, damit die Datei nicht riesig wird. Zwei Hauptvarianten:
  - **LongGOP** — sparsam: speichert nur ein vollständiges Bild und danach nur die Veränderungen. Kleine Dateien, ressourcenschonend, gut für Streaming/Aufnahme. **Das nutzen wir.**
  - **ALL-Intra** — jedes Bild komplett gespeichert. Bessere Qualität für Schnitt, aber riesige Dateien und sehr hohe Anforderungen an die Speicherkarte. **Nutzen wir nicht** (s. Hinweis unten).
- **4:2:2 / 4:2:0 10-Bit** — beschreibt, wie viel Farbinformation gespeichert wird. `4:2:2` hat mehr Farbdetails als `4:2:0`. `10-Bit` = feinere Farbabstufungen als 8-Bit (weniger Banding im Himmel etc.). Für Streaming reicht `4:2:0 10-Bit` problemlos.
- **Bitrate** (`Mbps` = Megabit pro Sekunde) — wie viele Daten pro Sekunde geschrieben werden. Mehr Mbps = bessere Qualität, aber mehr Speicherverbrauch und höhere Anforderungen an die SD-Karte. Faustregel: `100 Mbps` füllt eine 256-GB-Karte in ~5,5 h, `200 Mbps` in ~2,8 h.

> **Hinweis zu ALL-Intra-Modi (400/600 Mbps):** Diese Modi tauchen im Kameramenü auf, sind aber mit der vorhandenen V60-SD-Karte **nicht nutzbar** — die Karte ist zu langsam, die Aufnahme würde sofort abbrechen. Die Tabellen unten listen daher nur die mit V60 nutzbaren LongGOP-Modi.

#### Seite 1/6 — Open Gate / 6K / 5.9K (Full-frame, höchste Auflösungen)

| Auflösung | Seitenverh. | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|---|
| 5952×3968 | 3:2 (Open Gate) | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 5952×3136 | 17:9 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 5888×3312 | 16:9 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 200 Mbps |

> Im Menü erscheint `5888×3312 16:9` zweimal hintereinander — das ist ein bekanntes Anzeige-Verhalten (vermutlich H.264- und H.265-Variante derselben Auflösung). Für unsere Zwecke gleichwertig.

#### Seite 2/6 — APS-C 3.3K (Open Gate 4:3)

| Auflösung | Seitenverh. | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|---|
| 3328×2496 | 4:3 (Open Gate) | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |
| 3328×2496 | 4:3 (Open Gate) | APS-C | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |

#### Seite 3/6 — C4K (4096×2160, Cinema 4K, 17:9)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 4096×2160 | Full-frame | 50p | 4:2:2 10-Bit LongGOP | 200 Mbps |
| 4096×2160 | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 4096×2160 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 4096×2160 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |

#### Seite 4/6 — 4K UHD (3840×2160, 16:9)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 3840×2160 | APS-C | 50p | 4:2:2 10-Bit LongGOP | 200 Mbps |
| 3840×2160 | APS-C | 50p | 4:2:0 10-Bit LongGOP | 200 Mbps |
| 3840×2160 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 3840×2160 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 150 Mbps |

#### Seite 5/6 — FHD 100p (High Frame Rate, für Zeitlupe)

`100p` bedeutet 100 Bilder pro Sekunde. In der Wiedergabe mit 25p ergibt das eine 4×-Zeitlupe. Für normales Streaming nicht relevant.

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 1920×1080 | Full-frame | 100p | 4:2:2 10-Bit LongGOP | 150 Mbps |
| 1920×1080 | Full-frame | 100p | 4:2:0 10-Bit LongGOP | 150 Mbps |
| 1920×1080 | Full-frame | 50p | 4:2:2 10-Bit LongGOP | 100 Mbps |
| 1920×1080 | Full-frame | 50p | 4:2:0 10-Bit LongGOP | 100 Mbps |

#### Seite 6/6 — FHD 25p (sparsamster Modus, ideal als Backup-Aufnahme)

| Auflösung | Bildbereich | Bildrate | Codec | Bitrate |
|---|---|---|---|---|
| 1920×1080 | Full-frame | 25p | 4:2:2 10-Bit LongGOP | 100 Mbps |
| 1920×1080 | Full-frame | 25p | 4:2:0 10-Bit LongGOP | 100 Mbps |

### Stresstest-Modi für die Kirchen-Kamera

Ziel eines Stresstests: prüfen, wie lange die Kamera bei voller Last durchhält, **bevor** sie im echten Stream einsetzbar ist. Wir nutzen dafür interne SD-Aufnahme (kein Streaming-Pfad nötig).

> **Setup-Annahme:** Aktuell ist eine **V60-SD-Karte** im Einsatz. Die Tabelle und Empfehlung beziehen sich ausschließlich auf Modi, die mit V60 zuverlässig laufen.

#### Last-Profile sortiert nach erwarteter Wärme/Belastung

| Rang | Modus | Was wird belastet? | Dauer auf 256 GB |
|---|---|---|---|
| 1 | **6K Open Gate 25p LongGOP 200 Mbps (Full-frame 3:2)** | Maximaler Sensor-Readout (mehr Pixel als 5.9K) | ~170 Min (2,8 h) |
| 2 | 5.9K 25p LongGOP 200 Mbps (Full-frame 16:9) | Voller Sensor-Readout | ~170 Min (2,8 h) |
| 3 | 4K UHD 50p LongGOP 200 Mbps (APS-C) | Doppelte Framerate → mehr Encoder-Arbeit | ~170 Min (2,8 h) |
| 4 | C4K 50p LongGOP 200 Mbps (Full-frame) | Voller Sensor + 50p | ~170 Min (2,8 h) |

> Erklärung: "Sensor-Readout" = wie viele Pixel pro Sekunde der Bildsensor ablesen muss. Mehr Pixel oder höhere Framerate = mehr Wärme im Sensor. "Encoder-Arbeit" = wie viel die Kamera-Elektronik komprimieren muss. 50p doppelt so viel wie 25p.

#### Empfohlener Modus für den Hauptdurchlauf

**6K Open Gate 25p LongGOP 200 Mbps Full-frame**

| Parameter | Einstellung |
|---|---|
| Systemfrequenz | 50,00 Hz (PAL) |
| Aufnahmeformat | MOV |
| Aufnahmequalität | 5952×3968 3:2 Open Gate, 25p, 4:2:0 10-Bit LongGOP, 200 Mbps |
| Bildbereich | Full-frame |
| Erwartete Dauer auf 256 GB | ~170 Min (2,8 h) |

Begründung:
- 3:2 Open Gate liest mehr Sensorpixel als 5.9K 16:9 → härtester Sensor-Stress, der mit V60 stabil bleibt
- Lange Laufzeit deckt einen realistischen Gottesdienst-Marathon ab
- Geht über bisherigen 4K-Test (2×3,5 h bestanden, 2026-05-21) hinaus, weil der Sensor mehr arbeiten muss

**Optionaler zweiter Durchlauf (Encoder stärker fordern):** 4K UHD 50p LongGOP 200 Mbps APS-C — doppelte Framerate, stärkerer Encoder-Anteil.

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
