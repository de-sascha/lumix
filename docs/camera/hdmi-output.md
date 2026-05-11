# HDMI-Output-Einstellungen — Panasonic Lumix DC-S5IIX

## Übersicht

Die S5IIX gibt über den HDMI-A-Anschluss (Full-Size HDMI) ein Clean-Signal an die Blackmagic DeckLink Mini Recorder 4K aus.

## HDMI-Output-Konfiguration

### Menüpfad

**Setup-Menü > EIN/AUS > HDMI**

### Empfohlene Einstellungen

| Einstellung | Wert | Begründung |
|---|---|---|
| HDMI Mode Output | Auto / 4K | DeckLink 4K unterstützt bis 4K |
| Info Display HDMI | **OFF** | Clean Output ohne Overlays |
| HDMI Recording Control | OFF | DeckLink braucht kein HDMI-Trigger |
| Down Convert | OFF (bei 4K) / ON (bei 1080p) | Je nach gewünschter Ausgabe |

### Info Display HDMI: OFF ist KRITISCH

Wenn "ON": Alle Kamera-Informationen (Blende, ISO, Fokus-Rahmen, Histogramm) werden im HDMI-Signal eingeblendet → **NICHT für Streaming verwenden!**

## 4K vs. 1080p Output — Entscheidungshilfe

### 4K Output (3840×2160) an DeckLink

**Vorteile:**
- Digitales Cropping/Punch-in in OBS möglich (bis 200% = immer noch 1080p nativ)
- Höhere Bildqualität als Basis für 1080p-Downscale
- Flexibilität bei Bildausschnitt-Änderungen während des Streams

**Nachteile:**
- Etwas mehr Wärmeentwicklung in der Kamera
- Höhere GPU-Last in OBS (Downscale)
- DeckLink muss 4K verarbeiten

### 1080p Output (1920×1080) an DeckLink

**Vorteile:**
- Weniger Wärme in der Kamera
- Geringere System-Last in OBS
- Einfachere Pipeline

**Nachteile:**
- Kein digitales Cropping ohne Qualitätsverlust
- Festgelegter Bildausschnitt

### Empfehlung für Kirchenstreaming

**4K Output → OBS Downscale auf 1080p Stream**

Begründung: Die Möglichkeit, während des Gottesdienstes digital in das Bild hineinzuzoomen (z.B. vom Weitwinkel-Gesamtbild auf Prediger-Closeup), ist extrem wertvoll bei einem Einzelkamera-Setup. Bei 4K-Input kann OBS bis 2× zoomen und liefert trotzdem native 1080p-Qualität.

## HDMI-Farbtiefe und Farbraum

### Für Streaming (Rec.709)

| Parameter | Einstellung |
|---|---|
| Farbtiefe HDMI | 4:2:2 10-Bit |
| Farbraum/Gamma | Rec.709 (über Bildstil Standard/Natural) |
| Photo Style | Standard oder Natural |

**KEIN V-Log über HDMI für Live-Streaming!** → V-Log erfordert LUT-Verarbeitung in OBS.

### Für Recording auf externem Recorder (falls später erwünscht)

| Parameter | Einstellung |
|---|---|
| RAW-Datenausgabe über HDMI | ON (nur mit kompatibler Hardware) |
| Kompatibler Recorder | Atomos Ninja V/V+, BM Video Assist 5"/7" 12G HDR |
| Qualität | ProRes RAW oder Blackmagic RAW |

## Blackmagic DeckLink Mini Recorder 4K — Konfiguration

### Desktop Video Setup (Windows)

1. **Blackmagic Desktop Video Setup** installieren (Teil der Desktop Video Software)
2. Input-Einstellung: **HDMI** (nicht SDI — DeckLink hat nur einen Input aktiv!)
3. Video-Format: Auf "Auto" oder manuell auf das passende Format setzen

### Empfohlene DeckLink-Einstellungen

| Parameter | Wert |
|---|---|
| Input Connector | HDMI |
| Video Input | Auto-detect (oder 2160p25 / 1080p25 manuell) |
| Audio Input | HDMI (Embedded) |
| Color Space | Auto |

### Wichtig: Nur EIN Input gleichzeitig!

Die DeckLink Mini Recorder 4K hat zwar HDMI UND SDI-Eingänge, aber **es kann nur EINER gleichzeitig aktiv sein**. Für Multi-Cam müssen zusätzliche Capture-Karten oder NDI verwendet werden.

## HDMI-Kabel-Empfehlung

| Anforderung | Kabel-Typ |
|---|---|
| 4K 25p 4:2:2 10-Bit | HDMI 2.0 Kabel (High Speed, 18 Gbps) |
| Länge bis 5m | Standard HDMI-Kabel ausreichend |
| Länge 5-15m | Aktives HDMI-Kabel oder Glasfaser-HDMI |
| Kabelverriegelung | Empfohlen (Smallrig Clamp oder ähnlich) |

### Sicherung des HDMI-Kabels

- HDMI-Stecker an der Kamera ist empfindlich
- **Kabelhalter/Clamp** am Kamera-Cage oder Stativ-Platte befestigen
- Zugentlastung schaffen → verhindert Kabelauszug bei versehentlichem Zug
- Alternativ: Smallrig HDMI Cable Clamp für S5IIX

## Troubleshooting

| Problem | Lösung |
|---|---|
| Kein Signal auf DeckLink | HDMI-Input in Desktop Video Setup prüfen (nicht SDI) |
| Signal mit Overlays | Info Display HDMI auf OFF setzen |
| Falsche Auflösung | HDMI Mode Output und DeckLink-Format abgleichen |
| Kein Audio | Audio Input im Desktop Video auf "Embedded" |
| Schwarzes Bild nach Sleep | Alle Power-Save-Modi deaktivieren |
| Signal-Aussetzer | Kabel prüfen, bei >5m aktives Kabel verwenden |
