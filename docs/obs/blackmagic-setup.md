# Blackmagic DeckLink Mini Recorder 4K — Setup

## Hardware-Überblick

| Parameter | Wert |
|---|---|
| Modell | DeckLink Mini Recorder 4K |
| Interface | PCIe x4 (1 Lane) |
| Eingänge | 1× HDMI 2.0, 1× 6G-SDI |
| **Aktiver Eingang** | **Nur EINER gleichzeitig!** (HDMI ODER SDI) |
| Max. Auflösung | 4K (2160p) bis 30fps |
| Max. FHD | 1080p bis 60fps |
| Audio | 16 Kanäle eingebettet |
| Farbtiefe | 10-bit YUV 4:2:2 |
| Stromversorgung | Bus-powered (PCIe Slot, kein extra Strom nötig) |

## Hosanna-Konfiguration (aktuell) `[VERIFIZIERT]`

| Einstellung | Wert |
|---|---|
| **Aktiver Eingang** | **SDI** (von PTZ-Kamera AW-HE40HW) |
| Input Format | 1080i59.94 oder 1080p29.97 |
| HDMI Input | **Nicht verwendet** (reserviert für S5IIX) |
| Color Space | Rec. 709 |
| Desktop Video Version | v15.3.1 |

### Zwei-Kamera-Szenario (Zukunft: S5IIX + PTZ)

Da die DeckLink nur **einen Input gleichzeitig** nutzen kann:

| Lösung | Kamera auf DeckLink | Zweite Kamera |
|---|---|---|
| **Option A** | S5IIX → HDMI | PTZ → Mirabox USB (Downgrade) |
| **Option B** | PTZ → SDI (wie jetzt) | S5IIX → zweite DeckLink / USB Capture |
| **Option C** | S5IIX → HDMI | PTZ → NDI (via IP-Funktion der AW-HE40) |

> **Empfehlung:** Option C — PTZ hat native IP/RTSP-Fähigkeit. Die S5IIX liefert über HDMI die bessere Bildqualität und bekommt den DeckLink-Slot.

## Software-Installation

### 1. Blackmagic Desktop Video installieren

1. Download: blackmagicdesign.com > Support > Desktop Video
2. Installieren (erfordert Neustart)
3. Nach Neustart: **Blackmagic Desktop Video Setup** öffnen

### 2. Desktop Video Setup konfigurieren

**Für S5IIX (HDMI-Betrieb):**

| Einstellung | Wert |
|---|---|
| Input | **HDMI** |
| Video Standard | Auto Detect |
| Audio Input | Embedded |

**Für PTZ-Kamera (SDI-Betrieb, aktuell in Hosanna):**

| Einstellung | Wert |
|---|---|
| Input | **SDI** |
| Video Standard | Auto Detect |
| Audio Input | Embedded |
| Detected Format | 1080i59.94 SDI |

### 3. Verbindung prüfen

- Kamera einschalten mit HDMI-Kabel
- In Desktop Video Setup: Vorschau-Bild muss sichtbar sein
- Format wird automatisch erkannt (z.B. "2160p25")

## OBS-Integration

### Blackmagic-Quelle hinzufügen (S5IIX via HDMI)

1. OBS > Quellen > **+** > **Blackmagic Device** (oder "Video Capture Device" falls nicht aufgelistet)
2. **Device:** DeckLink Mini Recorder 4K
3. **Mode:** Auto (oder manuell: 2160p25 / 1080p25 je nach Kamera-Output)
4. **Video Format:** Passend zum HDMI-Output der Kamera
5. **Pixel Format:** Auto (10-bit wenn verfügbar)
6. **Color Space:** BT.709
7. **Color Range:** Full
8. **Audio:** Aktivieren falls HDMI-Audio genutzt wird

### Blackmagic-Quelle (PTZ via SDI — aktuell in Hosanna) `[VERIFIZIERT]`

| Parameter | Wert |
|---|---|
| OBS Source Name | "Panasonic CAM" |
| Type | Blackmagic Device |
| Device | DeckLink Mini Recorder 4K |
| Video Connection | SDI |
| Audio Connection | Embedded SDI |
| Mode | Auto Detect |
| Pixel Format | 8-bit YUV |
| Color Space | BT.709 |
| Color Range | Full |
| Buffering | Enabled |
| Deinterlace | Yadif (2x) — da PTZ 1080i liefert |

### Unterstützte Formate

| Auflösung | FPS | Unterstützt |
|---|---|---|
| 3840×2160 | 25p | Ja |
| 3840×2160 | 29.97p | Ja |
| 3840×2160 | 50p | **Nein** (4K max 30p) |
| 1920×1080 | 25p | Ja |
| 1920×1080 | 50p | Ja |
| 1920×1080 | 59.94p | Ja |

### Empfehlung für Kirchenstreaming

**Kamera-Output: 4K 25p (3840×2160 @ 25fps über HDMI)**
- DeckLink nimmt 4K25p entgegen
- OBS downscaled auf 1080p für den Stream
- Ermöglicht digitales Cropping ohne Qualitätsverlust

## Troubleshooting

| Problem | Lösung |
|---|---|
| OBS zeigt "No signal" | Desktop Video Setup prüfen: Input auf HDMI? |
| Kein Audio in OBS | Audio-Checkbox in der DeckLink-Quelle aktivieren |
| Falsche Farben | Photo Style auf Standard/Natural (kein V-Log ohne LUT) |
| Bild flackert | Shutter-Speed auf 1/50s (PAL) sicherstellen |
| OBS stürzt ab | Desktop Video Software und OBS auf aktuelle Version |
| Format nicht erkannt | In Desktop Video: Video Standard auf Auto Detect |
| Schwarzes Bild nach Standby | Kamera-Sleep deaktivieren, HDMI-Kabel neu stecken |

## Multi-Cam-Erweiterung

Da die DeckLink nur **einen Input** gleichzeitig nutzen kann, gibt es für Multi-Cam:

1. **Zweite DeckLink Mini Recorder 4K** im PC (benötigt zweiten PCIe-Slot)
2. **USB Capture Card** (z.B. Elgato Cam Link 4K) für die zweite Kamera
3. **NDI über LAN** (separater NDI-Encoder pro Kamera)

Für die aktuelle Einzelkamera-Lösung: DeckLink via HDMI ist die optimale Wahl.
