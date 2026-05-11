# Netzwerk & Streaming-Architektur

## Aktuelle Netzwerk-Infrastruktur

| Parameter | Wert |
|---|---|
| ISP | Vodafone Cable |
| Download | 1 Gbit/s |
| Upload | 50 Mbit/s |
| LAN | Gigabit Ethernet (Switch vorhanden) |
| Anbindung OBS-PC | Kabel (Gigabit LAN) |

## Streaming-Optionen mit der S5IIX

### Option A: HDMI → DeckLink → OBS (AKTUELL)

```
┌─────────┐    HDMI     ┌──────────────┐    PCIe    ┌─────────┐
│ S5IIX   │────────────│ DeckLink     │───────────│ OBS PC  │──→ Internet
│         │            │ Mini Rec 4K  │           │         │
└─────────┘            └──────────────┘           └─────────┘
```

**Vorteile:** Höchste Qualität, geringe Latenz, 4K 4:2:2 10-Bit
**Nachteile:** Kabel-basiert, max. Kabelstrecke 15m (aktives HDMI)

### Option B: Native Streaming-Funktion der S5IIX (RTMP/RTMPS)

Die S5IIX (nicht die S5II!) hat eine eingebaute Streaming-Funktion:

```
Kamera-Menü: Setup-Menü > EIN/AUS 1 > Streaming
```

| Einstellung | Optionen |
|---|---|
| Streaming-Funktion | ON/OFF |
| Streaming-Methode | Direkt |
| Verbindungsmethode | USB-Tethering / Wi-Fi / LAN |
| Streaming-Qualität | Bis FHD 6M 29.97p (H.264) |
| Plattformen | YouTube, Facebook, RTMP/RTMPS generisch |

**Limitierung:** Max. FHD 6Mbit — deutlich geringere Qualität als HDMI→DeckLink!

**Nur sinnvoll für:**
- Mobile Events ohne OBS-PC
- Zweite Kamera als Backup-Stream direkt zu YouTube
- Situationen wo kein HDMI-Kabel möglich ist

### Option C: NDI über LAN (Multi-Cam Zukunft)

Für zukünftige Multi-Kamera-Setups über das Gigabit-LAN:

```
┌─────────┐  HDMI  ┌──────────┐  LAN   ┌────────┐
│ Kamera 1│───────│ NDI      │────────│        │
│ (S5IIX) │       │ Encoder  │        │ OBS PC │──→ Internet
└─────────┘       └──────────┘   ┌───│ (NDI   │
                                 │   │ Recv.) │
┌─────────┐  HDMI  ┌──────────┐ │   └────────┘
│ Kamera 2│───────│ NDI      │─┘
│         │       │ Encoder  │
└─────────┘       └──────────┘
```

**NDI-Encoder-Optionen:**
- BirdDog Mini (HDMI → NDI)
- Magewell Pro Convert (HDMI → NDI)
- Kiloview N40 (HDMI → NDI)

**Vorteile NDI:**
- Nur ein Ethernet-Kabel pro Kamera
- Bis zu 100m Kabelstrecke (Standard Cat6)
- Multi-Cam ohne PCIe-Erweiterung
- Kamera-Steuerung möglich (PTZ-artig, je nach Encoder)

**Nachteile NDI:**
- Zusätzliche Hardware-Kosten (200-500€ pro Encoder)
- Leicht höhere Latenz als HDMI direkt
- NDI benötigt Bandbreite (~100-150 Mbit pro 1080p Stream auf LAN)

### Option D: SRT über LAN (Alternative zu NDI)

```
┌─────────┐  HDMI  ┌──────────┐  LAN   ┌────────┐
│ Kamera  │───────│ SRT      │────────│ OBS PC │
│ (S5IIX) │       │ Encoder  │        │(SRT In)│
└─────────┘       └──────────┘        └────────┘
```

**SRT-Vorteile gegenüber NDI:**
- Weniger Bandbreite nötig (konfigurierbare Bitrate)
- Robuster bei nicht-perfekter Netzwerk-Infrastruktur
- Kann auch über WAN/Internet funktionieren

**SRT-Encoder:**
- Magewell Ultra Encode HDMI
- Kiloview E1/E2

## Empfehlung: Aktuelle Architektur

Für **Einzelkamera-Streaming** ist die aktuelle Lösung (HDMI → DeckLink → OBS) optimal:

- Beste Qualität (4K 4:2:2 10-Bit)
- Geringste Latenz
- Zuverlässig (keine Netzwerk-Abhängigkeit für Kamera→PC)
- Keine zusätzliche Hardware nötig

## Multi-Cam-Erweiterung (Zukunft)

Wenn eine zweite Kamera hinzukommt:

| Option | Kosten | Qualität | Komplexität |
|---|---|---|---|
| Zweite DeckLink PCIe | ~170€ | Höchste | Niedrig (gleiche Pipeline) |
| NDI Encoder + NDI in OBS | ~300-500€ | Hoch | Mittel |
| SRT Encoder + SRT in OBS | ~300-500€ | Hoch | Mittel |
| USB Capture Card (Cam Link) | ~130€ | Gut (1080p) | Niedrig |

**Empfehlung für Multi-Cam:** Zweite DeckLink oder USB-Capture-Card für einfachste Integration.

## Bandbreiten-Kalkulation

### Upload-Budget (50 Mbit/s)

| Verwendung | Bandbreite | % des Upload |
|---|---|---|
| YouTube Stream 1080p25 | 8-12 Mbit | 16-24% |
| Puffer für Schwankungen | 10-15 Mbit | 20-30% |
| Andere Geräte im Netzwerk | 5-10 Mbit | 10-20% |
| **Verfügbar/Reserve** | **~15-25 Mbit** | **30-50%** |

**Fazit:** Bei 50 Mbit Upload ist ein 1080p-Stream mit 8-12 Mbit sehr komfortabel. Selbst 4K-Streaming (20-35 Mbit) wäre technisch möglich, lässt aber wenig Reserve.

### Empfehlung

- Während des Streams: Kein anderes Gerät im Netzwerk sollte Upload-intensiv arbeiten
- QoS am Router aktivieren (Priorisierung des OBS-PCs)
- Kabel-Verbindung für OBS-PC (KEIN WLAN!)
- Speed-Test vor dem Gottesdienst durchführen
