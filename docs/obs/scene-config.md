# OBS Szenen-Konfiguration — Hosanna Gottesdienst

## Signal-Flow (Gesamtarchitektur) `[VERIFIZIERT]`

```
                              ┌─── NDI Path (Primär für Livestream) ────┐
                              │                                         │
┌──────────────┐              │                                         ▼
│   Beamer PC  │──── NDI ─────┘                                ┌──────────────────┐
│  (SongBeamer)│                                               │  Livestream PC   │
│              │                                               │   (OBS Studio)   │
│  NDI Output: │         ┌──────────────────┐                  │                  │
│  "SongBeamer"│  HDMI   │  FeinTech Matrix  │  HDMI           │ Quellen:         │
│              ├────────▶│  VMS04201 (4x2)  ├────────┐         │ • NDI (Primär)   │
└──────────────┘         │  Input 1 → Out A │        │         │ • Mirabox USB    │
                         └──────────────────┘        ▼         │   (Fallback)     │
                                              ┌─────────────┐  │ • DeckLink SDI   │
                                              │   Mirabox   │  └────────┬─────────┘
                                              │  Capture    │           │
                                              │  Card       ├──USB 3.0──┘
                                              └──────┬──────┘  (Y-Kabel)
                                                     │ HDMI
                                                     │ Passthrough
                                                     ▼
┌──────────────┐   SDI   ┌──────────────────┐  ┌──────────────┐
│  PTZ Camera  ├────────▶│ Blackmagic       │  │  Projektor   │
│  AW-HE40HW  │         │ DeckLink Mini 4K │  │  TT-BW730    │
└──────────────┘         └─────────┬─────────┘  └──────────────┘
                                   │ PCIe
                                   ▼
                         Livestream PC (siehe oben)
```

## Zwei parallele Präsentations-Pfade

| Pfad | Route | Zweck | Latenz |
|------|-------|-------|--------|
| **NDI** (Primär) | Beamer PC → LAN → Livestream PC | Text/Slides für OBS-Szenen | Sehr gering (~1 Frame) |
| **HDMI/Mirabox** (Passthrough) | Beamer PC → Matrix → Mirabox → Projektor | Projektor-Anzeige + USB-Fallback | Null (Passthrough) |

Die Mirabox hat eine **Doppelrolle:**
1. HDMI-Passthrough zum Projektor (immer aktiv)
2. USB-Capture-Fallback für den Livestream PC (wenn NDI nicht verfügbar oder für Video-Content)

---

## OBS Source-Mapping

| OBS Source Name | Type | Device/Path | Verwendung |
|---|---|---|---|
| "Beamer NDI Texte" | NDI (DistroAV) | BEAMERPC (SongBeamer) | Liedtexte, Predigtfolien |
| "Beamer Screen" | NDI (DistroAV) | BEAMERPC (SongBeamer) | Vollbild inkl. Video-Playback |
| "Songbeamer klassisch (kein NDI)" | DirectShow | Mirabox USB | Fallback wenn NDI ausfällt |
| "Panasonic CAM" | Blackmagic Device | DeckLink SDI Auto-Detect | PTZ-Kamerabild |

---

## Scene Collection: "Hosanna Gottesdienst"

### ANFANG/ENDE

| Szene | Zweck | Quellen |
|---|---|---|
| Livestream Start Video | Pre-Service Loop (Countdown + Musik) | Video-Datei, Audio |
| Livestream Ende Video | Post-Service (QR-Spenden, Abschied) | Video-Datei, Audio |

### LOBPREIS

| Szene | Zweck | Quellen |
|---|---|---|
| Lobpreis - Kamera Vollbild | Worship — Kamera fullscreen | Panasonic CAM |
| Lobpreis - unten dunkel überblendet | Kamera mit dunklem Gradient unten | Panasonic CAM + Color Gradient |
| Lobpreis - Glaubensbekenntnis | Kamera + Texteinblendung (Credo) | Panasonic CAM + Beamer NDI Texte |
| Lobpreis - Jesus Schild | Kamera + Bild-Overlay | Panasonic CAM + Image |
| Lobpreis - Videos zeigen | Worship-Hintergrundvideos | Video Source |

### PREDIGT

| Szene | Zweck | Quellen |
|---|---|---|
| Predigt - Kamera Vollbild | Predigt — Kamera fullscreen | Panasonic CAM |
| Predigt - Power Point / Folien | NDI-Präsentation fullscreen (Slides) | Beamer NDI Texte |
| Lobpreis - Vater Unser | Kamera + Text-Overlay (Vaterunser) | Panasonic CAM + Beamer NDI Texte |

### BIBEL

| Szene | Zweck | Quellen |
|---|---|---|
| Bibel Text unten | Kamera + Bibeltext am unteren Rand | Panasonic CAM + Beamer NDI Texte |
| Bibel als Text - Vollbild, schwarzer Hintergrund | Bibeltext fullscreen auf Schwarz | Beamer NDI Texte + Color Source |
| Bibel als Bild - Vollbild, dunkelviolett | Bibel-Bild (dunkelviolett) | Image Source |
| Bibel als Text - Vollbild transparent | Bibeltext mit transparentem BG | Beamer NDI Texte |
| Bibel als Text - Kamera klein unten rechts | Bibeltext + PiP-Kamera | Beamer NDI Texte + Panasonic CAM (skaliert) |
| Bibel als Text - links oben grau hinterlegt | Bibeltext grau hinterlegt | Beamer NDI Texte + Color Source |

### ANKÜNDIGUNGEN

| Szene | Zweck | Quellen |
|---|---|---|
| Ankündigungen - Vollbild | NDI-Präsentation fullscreen | Beamer NDI Texte |

### EXTRAS

| Szene | Zweck | Quellen |
|---|---|---|
| Beamer Videos zeigen | Mirabox-Passthrough (SongBeamer USB) | Songbeamer klassisch (kein NDI) |

---

## Scene Collection: "HEILIG Konferenz" (Variante)

Erweiterte Version für die HEILIG-Konferenz mit zusätzlichen Szenen:
- "Predigt - Extra-Kamera" (zusätzliche Kamera via DirectShow)
- "NDI-Video (aus Songbeamer)" und "Extra-Kamera (gut)" als zusätzliche Sources
- "Bibel Text unten" in der PREDIGT-Gruppe statt BIBEL
- Ansonsten identische Struktur

---

## Studio Mode

| Einstellung | Wert |
|---|---|
| Preview/Program Mode | Enabled |
| Scene Duplication | Enabled |
| Swap Scenes | Enabled |
| Transition | Swipe |
| Hotkey | Ctrl+Shift+Enter / Numpad + |
| Confirm on Exit | Enabled |
| Warn before starting stream | Enabled |

---

## NDI Output (OBS → Netzwerk)

OBS sendet das Program-Signal als NDI ins LAN — damit können andere Geräte im Netzwerk den Livestream empfangen:

| Einstellung | Wert |
|---|---|
| Main Output | Enabled |
| Output Name | "HDMI Kamera" |
| Preview Output | Disabled |
| Tally (Program) | Enabled |
| Tally (Preview) | Enabled |

---

## Integration der S5IIX (Erweiterung)

Wenn die S5IIX als zweite/primäre Kamera integriert wird:

### S5IIX als Hauptkamera (DeckLink HDMI)

```
┌──────────┐   HDMI    ┌───────────────────┐   PCIe   ┌─────────────┐
│  S5IIX   ├──────────▶│ DeckLink Mini 4K  ├─────────▶│ Livestream  │
│  (4K25p) │           │ (Input: HDMI)     │          │ PC (OBS)    │
└──────────┘           └───────────────────┘          └─────────────┘
```

- DeckLink Input auf **HDMI** umschalten (Desktop Video Setup)
- OBS Source "Panasonic CAM" → Video Connection auf **HDMI** ändern
- Format: **2160p25** (4K, PAL) oder **1080p25** (geringere Last)
- PTZ-Kamera muss dann über Mirabox USB oder NDI/RTSP angebunden werden

### Empfohlene OBS-Source-Einstellungen für S5IIX

| Parameter | Wert |
|---|---|
| Type | Blackmagic Device |
| Device | DeckLink Mini Recorder 4K |
| Video Connection | HDMI |
| Audio Connection | Embedded (oder None, wenn Scarlett 2i2 genutzt) |
| Mode | Auto Detect (oder HD 1080p 25) |
| Pixel Format | 10-bit YUV (best) oder 8-bit YUV |
| Color Space | BT.709 |
| Color Range | Full |

### Vorteile S5IIX gegenüber PTZ AW-HE40HW

| Kriterium | S5IIX | PTZ AW-HE40HW |
|---|---|---|
| Sensor | Full-Frame 24.2 MP | 1/2.3" |
| Low Light | Dual Native ISO 640/4000 | Begrenzt |
| Bildqualität | 4K 4:2:2 10-bit | 1080i, kleiner Sensor |
| AF | Phase Hybrid 779 Punkte | Kein Autofokus (manuell/Preset) |
| Tiefenunschärfe | Schönes Bokeh (F2-2.8) | Alles scharf (Deep DoF) |
| Remote Control | Nein (manuell oder LUMIX Tether) | Ja (IP/RS-422, Presets) |
| Schwenk/Neige | Nein (Stativ) | Ja (motorisiert) |

---

## Plugins installiert

| Plugin | Version | Zweck |
|---|---|---|
| DistroAV | 6.2.1 | NDI Source/Output (Nachfolger von obs-ndi) |
| NDI SDK | 6.3.2 | NDI Runtime Library |
| obs-ios-camera-source | — | iPhone als Kamera-Source (optional) |
| VLC Video | 3.0.20 | VLC Media Source Support |
| Blackmagic OBS Plugin | (inkl. Desktop Video) | Native DeckLink-Integration |

---

## Backup & Recovery

| Komponente | Pfad |
|---|---|
| Scene Collections | `%APPDATA%\obs-studio\basic\scenes\` |
| Profiles | `%APPDATA%\obs-studio\basic\profiles\` |
| Full Config | `%APPDATA%\obs-studio\` |
| Backup-Skript | `obs_backup.bat` (OneDrive Sync) |
| Restore-Skript | `obs_restore.bat` (OneDrive Sync) |
| Backup-Ziel | OneDrive → Livestream/OBS/OBS Backup/ |
