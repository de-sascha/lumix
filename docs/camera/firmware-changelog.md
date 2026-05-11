# Firmware-Changelog: Panasonic Lumix DC-S5IIX / DC-S5II

**Aktuell installiert (S5IIX):** Version 2.6 (23. Dezember 2025)

> **WICHTIGER HINWEIS:** Die Online-Dokumentation von Panasonic (für DC-S5M2/S5M2X) zeigt
> Firmware-Versionen bis 3.7. Die S5II und S5IIX haben **unterschiedliche Versionsnummern**
> für das gleiche Feature-Set. Die S5II-Versionen (1.1, 2.0, 2.2, 3.0, 3.1, 3.2, 3.4, 3.7)
> entsprechen NICHT 1:1 den S5IIX-Versionen.
>
> **Die S5IIX Firmware 2.6 enthält möglicherweise Features, die in der S5II als Version 3.x gelistet sind.**
> Dies muss durch direkte Prüfung am Gerät verifiziert werden.

> Einträge mit `[VERIFIZIERT]` — anhand Panasonic Online-Dokumentation oder Gerät bestätigt.
> Einträge mit `[ONLINE-MANUAL]` — aus dem offiziellen Online-Benutzerhandbuch extrahiert.
> Einträge mit `[TRAINING-WISSEN]` — basieren auf dem Kenntnisstand bis Anfang 2025.

---

## Firmware-Historie (S5II Online-Manual Versionen) `[ONLINE-MANUAL]`

Die folgende Liste stammt aus dem offiziellen deutschen Online-Handbuch der DC-S5M2-Serie:

### Version 3.7 (neueste im Online-Manual)

- **Digitales Richtmikrofon DMW-DMS1** Unterstützung (optionales Zubehör)
- Änderungen bei anderen Funktionen

### Version 3.4

- **LUMIX Flow** Integration (Verknüpfung mit LUMIX Flow App)
- **Fokusring-Funktion verbessert**
- **Verschlusszeitbegrenzer** hinzugefügt (neues Menü-Item)
- **Proxy-Aufzeichnung verbessert**
- Ergänzungen/Änderungen bei anderen Funktionen

### Version 3.2

- **Bildmarkierung verbessert**
- **Automatische Erkennung (AF) verbessert**
- **[XS] Bildgröße** hinzugefügt
- **[MP4(Lite)]** als Aufnahme-Dateiformat hinzugefügt
- **Zoom-Funktionalität** erweitert
- **Sicherheitsverbesserungen**
- **LUMIX Lab** neue Funktionen
- Menü-Ergänzungen

### Version 3.1

- **Bildstil-Funktionalität** geändert
- **Echtzeit-LUT** Funktion verbessert
- **LUT-Bibliothek** verbessert
- **RAW-Verarbeitung** verbessert
- **LUMIX Lab** Anbindung (neue Funktion)
- **Wi-Fi Frequenzbänder** Konfiguration hinzugefügt
- Ergänzungen/Änderungen bei anderen Funktionen

### Version 3.0

Großes Feature-Update:
- **Proxy-Video-Aufnahmen** Funktion hinzugefügt
- **Frame.io Camera to Cloud** Kompatibilität
- **SH Pre-Burst-Aufnahmen** Funktion hinzugefügt
- **Automatische Erkennung (AF)** verbessert
- **Bildstabilisator** verbessert
- Ergänzungen/Änderungen bei anderen Funktionen

### Version 2.2

- **AF-Punkt-Vergrößerung** für Fotoaufnahmen hinzugefügt
  - Funktioniert in AF-Modi 1-Feld+, 1-Feld und Punktfokussierung
  - Auf Fn-Taste registrierbar
- **Hochauflösender Modus** erweitert
- **MF-Lupe-Vergrößerungseinstellung** hinzugefügt
- Ergänzungen/Änderungen bei anderen Funktionen

### Version 2.0

- **AFC Live-View** hinzugefügt (Setup-Menü > Monitor/Display)
  - Standard: SPEED PRIORITY

### Version 1.1

- **AFC Live-View** hinzugefügt (erste Einführung)
- Menü-Ergänzungen

---

## S5IIX-spezifische Firmware-Historie `[TRAINING-WISSEN + VERIFIZIERT]`

### Version 2.6 — Dezember 2025 `[VERIFIZIERT via installierter Firmware]`

- Stabilität und Performance-Verbesserungen
- Sicherheitsupdates
- **TODO:** Prüfen welche Features aus S5II v3.x hier enthalten sind
  - [ ] Frame.io Camera to Cloud?
  - [ ] Proxy-Video-Aufnahmen?
  - [ ] SH Pre-Burst?
  - [ ] MP4(Lite)?
  - [ ] LUMIX Flow?
  - [ ] Verschlusszeitbegrenzer?
  - [ ] DMW-DMS1 Mikrofonunterstützung?

### Version 2.0 — ca. Mitte 2024 `[TRAINING-WISSEN]`

Großes Feature-Update:
- **RAW-Video-Ausgabe über HDMI** an externe Rekorder (Atomos Ninja V/V+, Blackmagic Video Assist 5"/7" 12G HDR)
- **Videoreparatur-Funktion** (Wiedergabemenü > Bild bearbeiten > Videoreparatur)
  - Rettet beschädigte Videodateien nach Stromausfall/Kartenentfernung
  - Erzeugt .mdt Dateien; MP4-Videos können NICHT repariert werden
- **Apple ProRes RAW** und **Blackmagic RAW** Unterstützung (S5IIX nativ seit Launch)
- S5II erhält ProRes RAW und BRAW nur mit kostenpflichtigem **Upgrade-Key DWW-SFU2** (200 EUR)
- Erweiterte Aufnahmequalitäten: 5.9K, 4.1K und 3.5K Videos in RAW-Formaten
- Verbesserter AF bei schwachem Licht

### Version 1.0 — Launch (Juni 2023) `[VERIFIZIERT]`

- Initiale Firmware
- Phase Hybrid AF (779 Messpunkte, 100% Sensorabdeckung)
- Integrierter Lüfter für zeitlich unbegrenzte Videoaufnahme
- Interne SSD-Aufzeichnung über USB-C
- Direkte Streaming-Funktion (RTMP/RTMPS) — **nur S5IIX**
- 6K 30p, 5.9K 30p, C4K/4K 60p, 4K 120p (APS-C Crop)
- Apple ProRes 422 HQ / 422 intern
- V-Log / V-Gamut vorinstalliert (kein Upgrade nötig, anders als S5II)

---

## PRÜFUNGSANLEITUNG: Features am Gerät verifizieren

Um zu prüfen, welche Features in der installierten Firmware 2.6 vorhanden sind:

| Feature | Menüpfad zum Prüfen |
|---|---|
| Frame.io | Setup > EIN/AUS > Frame.io (falls vorhanden) |
| Proxy-Video | Videomenü > Bildformat > Proxy-Aufnahme |
| SH Pre-Burst | Foto > Auslösermodus > SH Pre-Burst |
| MP4(Lite) | Videomenü > Bildformat > Aufnahme-Dateiformat |
| LUMIX Flow | Setup > EIN/AUS > LUMIX Flow |
| Verschlusszeitbegrenzer | Videomenü > Belichtung > Verschlusszeitbegrenzer |
| DMW-DMS1 | Setup > EIN/AUS > Mikrofon (mit angeschlossenem DMW-DMS1) |
| Echtzeit-LUT | Videomenü > Bildstil > Echtzeit-LUT |
| LUT-Bibliothek | Videomenü > Bildstil > LUT-Bibliothek |
| Wi-Fi Frequenzbänder | Setup > EIN/AUS > Wi-Fi > Frequenzband |
| Bildgröße XS | Fotomenü > Bildgröße > XS |

**Bitte am Gerät prüfen und dieses Dokument entsprechend aktualisieren!**

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
