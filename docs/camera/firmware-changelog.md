# Firmware-Changelog: Panasonic Lumix DC-S5IIX / DC-S5II

**Aktuell installiert (S5IIX):** **Version 2.7** (10. März 2026) — eingespielt am 2026-05-20
**Neueste verfügbare Version (S5IIX):** Version 2.7 — aktuell ✅

Quelle: https://av.jpn.support.panasonic.com/support/global/cs/dsc/download/ff/dl/s5m2x.html (abgerufen 2026-05-20)

> Einträge mit `[VERIFIZIERT]` — anhand offizieller Panasonic Update-Seite oder Gerät bestätigt.
> Einträge mit `[TRAINING-WISSEN]` — basieren auf dem Kenntnisstand bis Anfang 2025.

---

## S5IIX-spezifische Firmware-Historie `[VERIFIZIERT via Panasonic Support 2026-05-20]`

### Version 2.7 — 10. März 2026 `[VERIFIZIERT — installiert seit 2026-05-20]`

- **Unterstützung für Panasonic-Mikrofon DMW-DMS1**
- Kompatibel mit den neuen Funktionen der **LUMIX Flow App (Ver. 1.5+)**
- Verbesserte Betriebsstabilität
- Datei: `S5m2XV27.zip` (157.760.717 Bytes)
- Lokale Kopie: `firmware/S5m2XV27.zip`

### Version 2.6 — 23. Dezember 2025 `[VERIFIZIERT]`

- Bildecken-Bug bei aktiver Bildstabilisierung behoben (Teile der Bildecken konnten fehlen, wenn die Kamera bewegt wurde)
- Bug behoben: Aufgenommene Videos konnten je nach SD-Karte Rauschen enthalten

### Version 2.5 — 18. November 2025 `[VERIFIZIERT]`

- Bug behoben: Videoaufnahme stoppte, wenn die WLAN-Verbindung zu LUMIX Flow oder LUMIX Lab unterbrochen wurde
- Bug behoben: Kreisförmiges Rauschen auf dem Monitor, wenn APS-C-Linsen ohne Ausschalten der Kamera entfernt wurden

### Version 2.4 — 20. Oktober 2025 `[VERIFIZIERT]` — Großes Feature-Update

- **Verbesserte Kompatibilität**
  - Bluetooth-Kopplung mit DJI-Gimbals hinzugefügt (keine Garantie aller Funktionen)
  - Verbesserte Kompatibilität mit OM Digital Solutions Blitzgeräten
  - Verbesserte Kompatibilität mit Wechselobjektiv S-R100500 und Telekonvertern (DMW-STC14/STC20)
- **LUMIX Flow ab v1.3 unterstützt**
  - Externer Monitor: LUTs auf Live View anwendbar
  - Externer Monitor: mehrere Frame-Marker gleichzeitig anzeigbar
  - Externer Monitor: Fokusrahmen anzeigbar
  - ⚠ Bei drahtloser Verbindung (Wi-Fi) stoppt die Videoaufnahme, wenn Bluetooth oder die App geschlossen wird → für Streaming USB-Kabelverbindung nutzen
- **Erweiterte Fokusring-Bedienung**
  - Fokusring als Control Ring nutzbar (Tastenfunktionen zuweisbar) — kompatibles Objektiv erforderlich
  - Drehrichtung wählbar (im/gegen Uhrzeigersinn)
- **Neue Video-Funktion**
  - **Verschlusszeitbegrenzer** im Video-Menü hinzugefügt
- **Weitere Verbesserungen**
  - Konstante Vorschau bei Blitzbenutzung
  - Schnellerer Einschaltvorgang
  - 17:9 Seitenverhältnis für Proxy-Videos
  - ISO-Steuerung bei Blitz geändert
  - Blende von **F45 bis F90** einstellbar (L-Mount-Standard)
  - Gemeinsame Einträge im "My Menu" werden jetzt in Foto- und Video-Modus gespiegelt

### Version 2.3 — 15. Juli 2025 `[VERIFIZIERT]`

- Sicherheits-Update
- Verbesserte Betriebsstabilität
- Hinweis: LUMIX Tether muss auf Ver. 2.10+ aktualisiert werden

### Version 2.2 — 23. Januar 2025 `[VERIFIZIERT]` — Großes Feature-Update

- **Erweiterte Motiverkennung**
  - [FLUGZEUG] und [ZUG] zu den Erkennungsmodi hinzugefügt
  - [Zielbereich] für [AUTO] und [MOTORRAD] hinzugefügt
- **Mehrere Frame-Marker gleichzeitig anzeigbar** (bis zu 3)
- **Crop Zoom** hinzugefügt (zentraler Bildbereich, ohne Qualitätsverlust)
- **Hybrid Zoom** hinzugefügt (optisch + elektronisch nahtlos kombiniert)
- **MP4(Lite)** als Aufnahmeformat — 3.8K (3840x2560) 29.97p 50Mbps
- **Bildgröße [XS]** hinzugefügt (kleinere Dateigröße)
- **LUMIX Lab v1.3+ Features:** Remote Shooting, Shutter Remote, Wireless IP Streaming, Bildauswahl an der Kamera für Transfer
- ⚠ **Funktionen entfernt — kritisch für Streaming-Setup:**
  - **RTMP-Streaming entfernt (nur EU-Modelle!)**
  - **WLAN-Bildtransfer zum PC entfernt (nur EU-Modelle!)**
  - Wired LAN Streaming (RTP/RTSP) komplett entfernt
  - Wi-Fi-Direktverbindung erfordert immer Passwort-Authentifizierung ([Wi-Fi-Passwort]-Menü entfernt)
  - TKIP-Verschlüsselung nicht mehr unterstützt
  - "Keine Verschlüsselung"-Option für AP-Verbindungen entfernt

### Version 2.1 — 9. Oktober 2024 `[VERIFIZIERT]`

- **Neuer Photo Style: [LEICA Monochrome]**
- **LUMIX Lab Smartphone-App-Kompatibilität**
- **Panasonic XLR-Mikrofon-Adapter DMW-XLR2** unterstützt (32-bit Float **nicht** verfügbar bei diesem Modell)
- **5GHz-Wi-Fi-Frequenzband** als Option hinzugefügt (regionale Einschränkungen draußen beachten)
- [REAL TIME LUT] kann auf Fn-Taste gelegt werden
- Pop-up-Meldung bei einklappbaren Panasonic-Objektiven

### Version 2.0 — 22. April 2024 `[VERIFIZIERT]`

- **Frame.io Camera to Cloud** Kompatibilität (Upload von Stills + Proxy-Videos via Wi-Fi)
- **Proxy-Aufnahme** Funktion hinzugefügt (gleichzeitig mit Hauptvideo)
- **[SH PRE]** hinzugefügt (Pre-Burst-Aufnahmen ab halbem Auslöserdruck)
- **Verbesserte automatische Erkennung**
  - Bessere Tracking- und Personenerkennungs-Performance
  - [Zielbereich] und Augenerkennung für [TIER]
  - [AUTO] und [MOTORRAD] zu Auto-Erkennung hinzugefügt
- **Verbesserter Bildstabilisator**
  - [HIGH]-Stufe für E-Stabilisierung (Video) bei Bewegung
  - Perspektivverzerrungs-Korrektur bei Weitwinkel-Videos
- Bug behoben: rötlich-violette Färbung bei Live View Composite

### Version 1.5 — 30. Januar 2024 `[VERIFIZIERT]`

- Bug behoben: vertikale Linien bei JPEG-Aufnahmen mit i.Dynamic Range

### Version 1.4 — 20. Dezember 2023 `[VERIFIZIERT]`

- Verbesserte Stabilität bei einigen Speichergeräten
- Bug behoben: horizontale Linien bei JPEG im SH Burst Modus

### Version 1.3 — 24. Oktober 2023 `[VERIFIZIERT]`

- **[AF-Punkt-Lupe]** hinzugefügt (Vergrößerung der Fokusposition während AF)
- **Hochauflösender Modus** erweitert: Verschlusszeit bis 8 Sek., [Long Exposure NR] nutzbar
- **[Handheld High-Res]**-Modus hinzugefügt (max. 1 Sek. Verschlusszeit)
- **MF-Lupe-Vergrößerung** bis ca. 20-fach einstellbar
- Schnellere LCD/EVF-Umschaltung, bessere Sucher-Sicht zwischen Serienbild-Frames

### Version 1.2 — 22. August 2023 `[VERIFIZIERT]`

- Bug behoben: Färbung von Motiven und deren Konturen unter bestimmten Bedingungen

### Version 1.1 — 13. Juni 2023 `[VERIFIZIERT]`

- Verbesserte V-Log-Bildqualität
- Verbesserte Kompatibilität mit einigen SD-Karten
- Verbesserte Betriebsstabilität

### Version 1.0 — Launch (Juni 2023) `[VERIFIZIERT]`

- Initiale Firmware
- Phase Hybrid AF (779 Messpunkte, 100% Sensorabdeckung)
- Integrierter Lüfter für zeitlich unbegrenzte Videoaufnahme
- Interne SSD-Aufzeichnung über USB-C
- Direkte Streaming-Funktion (RTMP/RTMPS) — **nur S5IIX**, **in EU mit FW 2.2 entfernt**
- 6K 30p, 5.9K 30p, C4K/4K 60p, 4K 120p (APS-C Crop)
- Apple ProRes 422 HQ / 422 intern
- V-Log / V-Gamut vorinstalliert (kein Upgrade nötig, anders als S5II)

---

## In FW 2.7 enthaltene Features (verifiziert via offizieller Changelog-Historie)

Bei der installierten FW 2.7 sind alle Features bis einschließlich Version 2.7 enthalten:

| Feature | Eingeführt mit FW | In 2.7 vorhanden | Menüpfad |
|---|---|---|---|
| Frame.io Camera to Cloud | 2.0 | ✅ | Setup > EIN/AUS > Frame.io |
| Proxy-Aufnahme | 2.0 | ✅ | Videomenü > Bildformat > Proxy-Aufnahme |
| SH PRE (Pre-Burst) | 2.0 | ✅ | Foto > Auslösermodus > SH PRE |
| LEICA Monochrome | 2.1 | ✅ | Photo Style |
| LUMIX Lab Support | 2.1 | ✅ | App-seitig |
| DMW-XLR2 (kein 32-bit Float) | 2.1 | ✅ | XLR-Adapter anschließen |
| 5GHz Wi-Fi | 2.1 | ✅ | Setup > Wi-Fi > Frequenzband |
| Crop Zoom | 2.2 | ✅ | Foto/Video-Menü |
| Hybrid Zoom | 2.2 | ✅ | Foto/Video-Menü |
| MP4(Lite) | 2.2 | ✅ | Videomenü > Bildformat > Dateiformat |
| Bildgröße XS | 2.2 | ✅ | Fotomenü > Bildgröße > XS |
| Motiverkennung Flugzeug/Zug | 2.2 | ✅ | AF-Menü |
| LUMIX Flow App | 2.4 | ✅ | Setup > EIN/AUS > LUMIX Flow |
| Verschlusszeitbegrenzer | 2.4 | ✅ | Videomenü > Belichtung |
| Fokusring als Control Ring | 2.4 | ✅ | Custom > Objektiv/Sonstige |
| Blende F45–F90 | 2.4 | ✅ | Belichtung |
| DJI Gimbal Bluetooth-Pairing | 2.4 | ✅ | Setup > Bluetooth |
| **DMW-DMS1 Mikrofon** | **2.7** | ✅ | Setup > EIN/AUS > Mikrofon (mit angeschlossenem DMS1) |
| **LUMIX Flow v1.5+ Features** | **2.7** | ✅ | App-seitig |

---

## EU-spezifische Einschränkungen / Regionale Unterschiede

### Aufnahmedauer
- **Die S5IIX hat KEINE zeitliche Aufnahmebegrenzung** — der integrierte Lüfter ermöglicht unbegrenzte Aufnahmen
- Historisch hatten EU-Panasonic-Kameras ein 30-Minuten-Limit (Zollklassifizierung als "Videokamera"). Dies gilt für die S5IIX **NICHT** mehr

### Streaming-Funktion (nur S5IIX)
- ⚠ **WICHTIG (EU):** Mit FW 2.2 (Januar 2025) wurden in **EU-Modellen** folgende Funktionen **entfernt**:
  - **RTMP-Streaming via Wi-Fi/USB-Tethering**
  - **Wired LAN Streaming (RTP/RTSP)**
  - **WLAN-Bildtransfer zum PC**
- Vor FW 2.2 (also FW 1.0–2.1): RTMP/RTMPS via Wi-Fi, LAN oder USB-Tethering verfügbar — bis zu FHD | 6M | 29.97p (H.264), YouTube/Facebook/RTMP generisch
- **Ab FW 2.2 in EU:** Streaming nur noch via **LUMIX Lab App (Wireless IP Streaming, ab FW 2.2)** oder **LUMIX Flow App (ab FW 2.4)** möglich
- ❓ Status auf der installierten FW 2.6: zu verifizieren, ob RTMP-Menü noch vorhanden ist (bei EU-Geräten, die ab 2.2 aktualisiert wurden, ist es entfernt)

### Systemfrequenz in der EU
- **50.00 Hz (PAL)** — Standard für Europa
- Verfügbare Bildraten bei PAL: 25p, 50p, 100p
- 24.00 Hz (CINEMA) ist ebenfalls verfügbar: 24p, 48p
- **NTSC (59.94 Hz) kann ebenfalls eingestellt werden** — nötig, wenn NTSC-Livestreaming-Plattformen bessere Kompatibilität bieten

---

## Funktionen, die NICHT existieren / häufige Missverständnisse

| Funktion | Status | Anmerkung |
|---|---|---|
| Interne RAW-Aufnahme | NICHT vorhanden | RAW nur über HDMI an externen Rekorder |
| 4K 120p Full Frame | NICHT vorhanden | 4K 120p nur mit APS-C Crop |
| ProRes RAW intern | NICHT vorhanden | Nur Apple ProRes 422/422HQ intern |
| Dual Native ISO bei Video | VORHANDEN | Basiswerte: ISO 640 / ISO 4000 |
| IBIS + OIS Dual IS | EINGESCHRÄNKT | Nur mit kompatiblen Panasonic L-Mount Linsen (Dual I.S. 2) |
| LAN-Streaming | NUR S5IIX | Über USB-LAN-Adapter oder direkt über Streaming-Funktion |
| SSD Recording | VORHANDEN | Über USB-C an externe SSD |

---

## Firmware-Update-Prozess

1. Firmware von Panasonic-Support-Seite herunterladen
2. Auf formatierte SD-Karte im Root-Verzeichnis kopieren
3. Karte in Slot 1 einlegen
4. Kamera einschalten, Akku muss >50% sein
5. Setup-Menü > Sonstige > Firmware-Anz. > Update ausführen
6. NICHT während des Updates ausschalten!
7. Nach Update: LUMIX Lab, LUMIX Sync, LUMIX Flow und LUMIX Tether aktualisieren

---

## Begleit-Software (immer mit Firmware updaten)

| Software | Plattform | Zweck |
|---|---|---|
| LUMIX Lab | Smartphone | Bildbearbeitung, LUT-Transfer |
| LUMIX Sync | Smartphone | Fernsteuerung, Bildtransfer |
| LUMIX Flow | Smartphone | Workflow-Integration |
| LUMIX Tether | PC (Win/Mac) | Fernsteuerung vom Computer |
| LUMIX Webcam Software | PC (Win/Mac) | Kamera als USB-Webcam nutzen |
