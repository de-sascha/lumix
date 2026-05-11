# Firmware-Changelog: Panasonic Lumix DC-S5IIX

**Aktuell installiert:** Version 2.6 (23. Dezember 2025)

> **Hinweis:** Dieses Dokument wird kontinuierlich aktualisiert. Einträge, die mit
> `[VERIFIZIERT]` markiert sind, wurden anhand offizieller Panasonic-Release-Notes bestätigt.
> Einträge mit `[TRAINING-WISSEN]` basieren auf dem Kenntnisstand bis Anfang 2025.

---

## Version 2.6 — Dezember 2025 `[VERIFIZIERT via Kamera-Firmware]`

- Stabilität und Performance-Verbesserungen
- Sicherheitsupdates
- (Detaillierte Release Notes TODO: bei Panasonic prüfen)

## Version 2.4 — ca. Mitte 2025 `[TRAINING-WISSEN]`

- Verbesserungen der AF-Leistung
- Stabilitätsverbesserungen

## Version 2.2 — ca. Anfang 2025 `[TRAINING-WISSEN]`

- AF-Punkt-Vergrößerung für Fotoaufnahmen implementiert (S5II: v2.2, S5IIX: v1.3)
  - Funktioniert in AF-Modi 1-Feld+, 1-Feld und Punktfokussierung
  - Auf Fn-Taste registrierbar
- Verbessertes Tracking bei Gesichtserkennung

## Version 2.0 — ca. Mitte 2024 `[TRAINING-WISSEN]`

Großes Feature-Update:
- **RAW-Video-Ausgabe über HDMI** an externe Rekorder (Atomos Ninja V/V+, Blackmagic Video Assist 5"/7" 12G HDR)
- **Videoreparatur-Funktion** (Wiedergabemenü > Bild bearbeiten > Videoreparatur)
  - Rettet beschädigte Videodateien nach Stromausfall/Kartenentfernung
  - Erzeugt .mdt Dateien; MP4-Videos können NICHT repariert werden
- **Apple ProRes RAW** und **Blackmagic RAW** Unterstützung (S5IIX nativ seit Launch)
- S5II erhält ProRes RAW und BRAW nur mit kostenpflichtigem **Upgrade-Key DWW-SFU2** (200 EUR)
- Erweiterte Aufnahmequalitäten: 5.9K, 4.1K und 3.5K Videos in RAW-Formaten
- Verbesserter AF bei schwachem Licht

## Version 1.3 — ca. Ende 2023 `[TRAINING-WISSEN]`

- Erste größere Verbesserungen nach Launch
- AF-Performance-Optimierungen
- Stabilitäts-Fixes

## Version 1.0 — Launch (Juni 2023) `[VERIFIZIERT]`

- Initiale Firmware
- Phase Hybrid AF (779 Messpunkte, 100% Sensorabdeckung)
- Integrierter Lüfter für zeitlich unbegrenzte Videoaufnahme
- Interne SSD-Aufzeichnung über USB-C
- Direkte Streaming-Funktion (RTMP/RTMPS) — **nur S5IIX**
- 6K 30p, 5.9K 30p, C4K/4K 60p, 4K 120p (APS-C Crop)
- Apple ProRes 422 HQ / 422 intern
- V-Log / V-Gamut vorinstalliert (kein Upgrade nötig, anders als S5II)

---

## EU-spezifische Einschränkungen / Regionale Unterschiede

### Aufnahmedauer
- **Die S5IIX hat KEINE zeitliche Aufnahmebegrenzung** — der integrierte Lüfter ermöglicht unbegrenzte Aufnahmen
- Historisch hatten EU-Panasonic-Kameras ein 30-Minuten-Limit (Zollklassifizierung als "Videokamera"). Dies gilt für die S5IIX **NICHT** mehr

### Streaming-Funktion (nur S5IIX)
- Die eingebaute Streaming-Funktion (RTMP/RTMPS via Wi-Fi, LAN oder USB-Tethering) ist **nur in der S5IIX** verfügbar, nicht in der S5II
- Streaming-Qualität: bis zu FHD | 6M | 29.97p (H.264)
- Streaming-Methoden: Direkt (über Smartphone/USB-Tethering) oder LAN
- Unterstützte Plattformen: YouTube, Facebook, RTMP/RTMPS generisch

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
