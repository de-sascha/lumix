# Kapitel 3 — Firmware-Stand und Versionshistorie

> Teil I, Kapitel 3 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [2. Region und Systemfrequenz (im README)](../../README.md#2-region-und-systemfrequenz). Nächstes Kapitel: [4. Stromversorgung und Standby](power-management.md).

## Worum geht es hier?

Die Firmware ist die interne Software der Kamera. Panasonic veröffentlicht regelmäßig Updates, die neue Funktionen bringen oder Fehler beheben — manchmal aber auch **bestehende Funktionen entfernen**, gerade in der EU-Variante. Vor jedem Firmware-Update lohnt sich daher ein Blick in die Versionshistorie: bringt das Update etwas Nützliches? Nimmt es etwas weg, das wir aktuell verwenden?

**Was dieses Kapitel liefert:**

1. Den **aktuell installierten Firmware-Stand** (Abschnitt 3.1).
2. Was **konkret in unserer Version 2.7** alles enthalten ist (Abschnitt 3.2).
3. **Wichtige EU-spezifische Einschränkungen**, die man kennen muss (Abschnitt 3.3).
4. **Was die S5IIX nicht kann**, obwohl es oft falsch kolportiert wird (Abschnitt 3.4).
5. Den **Update-Prozess** Schritt für Schritt (Abschnitt 3.5).
6. Die **vollständige Versionshistorie** als Nachschlagewerk (Abschnitt 3.6).

> **Lese-Tipp:** Wer nur wissen will, was die aktuelle Firmware kann, liest 3.1–3.4. Die ausführliche Versionsliste in 3.6 ist Nachschlage-Material — z. B. interessant, wenn man eine ältere Kamera findet und wissen will, was seitdem passiert ist.

---

## 3.1 Aktueller Stand (Quick-Facts)

| Feld | Wert |
|---|---|
| **Installiert (S5IIX)** | **Version 2.7** (10. März 2026) — eingespielt am 2026-05-20 |
| **Neueste verfügbare Version** | Version 2.7 — also aktuell ✅ |
| Firmware-Quelle | https://av.jpn.support.panasonic.com/support/global/cs/dsc/download/ff/dl/s5m2x.html (abgerufen 2026-05-20) |
| Lokale Kopie der Datei | `firmware/S5m2XV27.zip` |

> **Verifikations-Hinweise in der Versionsliste:**
> - `[VERIFIZIERT]` — anhand der offiziellen Panasonic-Update-Seite oder am Gerät bestätigt.
> - `[TRAINING-WISSEN]` — basiert auf Kenntnisstand bis Anfang 2025, ohne Quellen-Bestätigung.

---

## 3.2 Was kann die Kamera jetzt? (Features in FW 2.7)

Bei FW 2.7 sind **alle** Features kumulativ enthalten — also alles, was zwischen Version 1.0 und 2.7 jemals dazugekommen ist. Hier eine Übersicht der praxisrelevanten Funktionen, sortiert danach, mit welcher Firmware-Version sie eingeführt wurden:

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

## 3.3 EU-spezifische Einschränkungen

Die EU-Variante der S5IIX unterscheidet sich von japanischen oder US-Versionen. Zwei Dinge sind wichtig zu wissen:

### Aufnahmedauer — keine 30-Minuten-Grenze mehr

Historisch hatten EU-Panasonic-Kameras ein 30-Minuten-Limit für Videoaufnahmen, weil sie sonst in der Zollklassifizierung als „Videokamera" statt „Fotokamera" eingestuft worden wären (= höhere Zölle). Bei der S5IIX **gilt das nicht mehr** — sie kann unbegrenzt aufnehmen, und der eingebaute Lüfter macht das auch praktisch möglich (siehe [Kapitel 5](thermal-management.md)).

### ⚠ Streaming-Funktion: in EU-FW 2.2 entfernt

Bei FW 2.2 (Januar 2025) hat Panasonic in **EU-Modellen** mehrere Streaming-relevante Funktionen **entfernt**:

- **RTMP-Streaming** via Wi-Fi/USB-Tethering — die Kamera konnte vorher direkt zu YouTube/Facebook streamen, ohne PC dazwischen
- **Wired LAN Streaming** (RTP/RTSP)
- **WLAN-Bildtransfer zum PC**
- Mehrere Wi-Fi-Sicherheits-Lockerungen (kein „ohne Verschlüsselung", kein TKIP, immer Passwort-Pflicht)

**Was heißt das für uns?** Bei uns ist Streaming sowieso über OBS auf einem PC gelöst — die fehlende eingebaute RTMP-Funktion betrifft uns also nicht direkt. **Aber:** Falls man jemals auf die Idee käme, ohne PC direkt aus der Kamera zu streamen (z. B. für einen mobilen Einsatz), geht das mit unserer EU-FW nicht mehr. Stattdessen ginge nur der Umweg über die Apps **LUMIX Lab** (ab FW 2.2) oder **LUMIX Flow** (ab FW 2.4).

### Systemfrequenz — immer PAL (50 Hz) in der EU

Details zu diesem Thema in [Kapitel 6 — Videoeinstellungen](video-settings.md). Kurz:

- **50,00 Hz (PAL)** ist Standard. Bildraten: 25p, 50p, 100p.
- 24,00 Hz (CINEMA): 24p, 48p — möglich, für Streaming nicht relevant.
- 59,94 Hz (NTSC): einstellbar, aber in der EU **wegen 50-Hz-Kunstlicht problematisch** (Flicker).

---

## 3.4 Was die S5IIX NICHT kann — häufige Missverständnisse

Im Internet kursieren zu jeder Kamera Behauptungen, die nicht stimmen. Für die S5IIX die häufigsten:

| Vermeintliches Feature | Status | Anmerkung |
|---|---|---|
| Interne RAW-Aufnahme | **Nicht vorhanden** | RAW gibt es nur über HDMI an einen externen Rekorder. |
| 4K 120p mit vollem Sensor | **Nicht vorhanden** | 4K 120p geht nur mit APS-C-Crop (= ~1,5×-Tele-Effekt). |
| ProRes RAW intern | **Nicht vorhanden** | Intern gibt es Apple ProRes 422 / 422 HQ, aber nicht ProRes RAW. |
| Dual Native ISO bei Video | ✅ Vorhanden | Basis-ISOs: **640** und **4000**. Erklärt in [Kapitel 15 — Best Practices](../streaming/best-practices.md). |
| IBIS + OIS Dual IS | ⚠ Eingeschränkt | „Dual I.S. 2" funktioniert nur mit kompatiblen Panasonic-L-Mount-Objektiven. Mit dem Samyang gibt es nur IBIS, nicht die Kombi. |
| LAN-Streaming | Nur S5IIX-Modell | Die nicht-X-Variante S5II hat das nie gehabt. Bei S5IIX in EU zudem mit FW 2.2 entfernt (siehe oben). |
| SSD-Aufnahme über USB-C | ✅ Vorhanden | Externe SSD per USB-C anschließbar — relevant für High-Bitrate-Aufnahmen. |

---

## 3.5 Firmware-Update-Prozess

Schrittweise durchgehen — ein Firmware-Update kann bei Stromausfall die Kamera unbenutzbar machen.

1. **Firmware herunterladen** von der Panasonic-Support-Seite (Link in Abschnitt 3.1).
2. Datei auf eine **frisch in der Kamera formatierte SD-Karte** kopieren — ins **Wurzelverzeichnis** (nicht in einen Unterordner).
3. Karte in **Slot 1** einlegen.
4. Kamera einschalten, Akku **muss > 50 %** sein. Idealerweise zusätzlich ein USB-PD-Netzteil anschließen.
5. **Setup-Menü → Sonstige → Firmware-Anz. → Update ausführen**
6. Während des Updates **NICHT ausschalten**, **NICHT die Karte ziehen**, **NICHT den Akku entnehmen**. Es dauert mehrere Minuten.
7. Nach Abschluss: zusätzlich **LUMIX Lab, LUMIX Sync, LUMIX Flow** und **LUMIX Tether** auf die jeweils neueste Version aktualisieren — sonst können App-Funktionen wegbrechen.

### Begleit-Software (immer mit der Firmware mitziehen)

| Software | Plattform | Zweck |
|---|---|---|
| LUMIX Lab | Smartphone | Bildbearbeitung, LUT-Transfer |
| LUMIX Sync | Smartphone | Fernsteuerung, Bildtransfer |
| LUMIX Flow | Smartphone | Workflow-Integration |
| LUMIX Tether | PC (Win/Mac) | Fernsteuerung vom Computer |
| LUMIX Webcam Software | PC (Win/Mac) | Kamera als USB-Webcam nutzen |

---

## 3.6 Vollständige Versionshistorie (Nachschlagewerk)

> Hinweis: Diese Liste ist als Referenz gedacht. Für den normalen Betrieb reichen Abschnitte 3.1–3.5.

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
