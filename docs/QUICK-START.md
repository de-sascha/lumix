# Schnellstart-Anleitung: Sonntagsgottesdienst

## 60 Minuten vor Beginn

### 1. Strom & Hardware aufbauen (15 Min.)

1. Stativ aufstellen und ausrichten
2. Kamera auf Stativ montieren
3. Samyang 35-150mm aufsetzen (oder 18-40mm für Weitwinkel)
4. USB-PD Netzteil an Steckdose → USB-C Kabel an Kamera
5. HDMI-Kabel an Kamera → DeckLink-Eingang am PC
6. Kamera einschalten — Lade-Symbol auf Display bestätigen

### 2. Kamera konfigurieren (10 Min.)

**Schnell-Einstellungen (falls nicht gespeichert):**

```
Modus-Rad:               M (Kreative Filme)
Systemfrequenz:          50 Hz (Setup > Sonstige > Systemfrequenz)
Shutter:                 1/50s
Blende:                  F2.8 (Samyang) / F4.5 (18-40mm)
ISO:                     Auto (100-6400)
Weißabgleich:            Kelvin manuell (3200-5000K je nach Kirche)
Bildstil:                Standard
```

**Menü-Einstellungen:**

| Menü | Einstellung | Wert |
|---|---|---|
| Setup > Monitor/Display 1 | Power Save Mode > Sleep | OFF |
| Setup > Monitor/Display 1 | Thermal Management | HIGH |
| Setup > EIN/AUS | Fan Mode | AUTO2 |
| Setup > EIN/AUS > HDMI | Info Display | OFF |
| Video > Fokus | Dauer-AF | MODE 1 |
| Video > Fokus | AF-Erkennungseinst. | ON |
| Video > Fokus | Motiverk.-Auswahl | FACE/EYE |

**AF-Modus:** Taste FF drücken → Zone (H/V) → auf Kanzel positionieren

### 3. OBS & Stream vorbereiten (10 Min.)

1. OBS starten (Scene Collection: "Hosanna Gottesdienst")
2. DeckLink-Quelle prüfen ("Panasonic CAM" — Bild sichtbar?)
3. NDI-Source prüfen ("Beamer NDI Texte" — SongBeamer verbunden?)
4. Audio "Mischpult" (Scarlett 2i2): Pegel vom Mischpult korrekt? **UNMUTE!**
5. Stream-Key prüfen (YouTube Studio, falls erneuert)
6. Lokale Aufnahme aktivieren (Fragmented MP4)
7. Studio Mode aktiv? (Preview/Program)

### 4. Test-Run (10 Min.)

1. **Test-Stream** starten (auf YouTube als "Nicht gelistet")
2. Auf Handy prüfen: Bild, Ton, Farben, Fokus
3. Durch den Raum gehen lassen — AF-Verhalten prüfen
4. OBS-Statistiken: 0 Dropped Frames?
5. Kamera-Temperatur stabil?
6. Test-Stream beenden

### 5. Bereit (5 Min. vor Beginn)

1. Bildausschnitt final einstellen
2. OBS-Szene auf "Standbild/Willkommen" setzen
3. Stream starten (Countdown-Grafik oder Standbild)
4. Lokale Aufnahme starten
5. Auf "Kamera Vollbild" wechseln wenn Gottesdienst beginnt

---

## Während des Gottesdienstes

### Aufgaben des Operators

| Aktion | Wann |
|---|---|
| Bildausschnitt anpassen (Zoom) | Bei Wechsel Prediger ↔ Chor |
| OBS-Szene wechseln | Bei Liedtext-Einblendung |
| Fokus überwachen | Kontinuierlich (AF sollte automatisch arbeiten) |
| OBS-Statistiken prüfen | Alle 15 Min. kurz auf Dropped Frames schauen |
| Belichtung nachjustieren | Bei starken Lichtwechseln |

### Bei Problemen während des Streams

| Problem | Sofort-Maßnahme |
|---|---|
| Bild weg (schwarz) | HDMI-Kabel prüfen → Kamera aus/ein |
| Fokus falsch | Touch auf richtige Person oder AF pausieren |
| Bild zu dunkel/hell | Belichtungskorrektur ±EV anpassen |
| Stream-Abbruch (OBS) | "Stream starten" erneut klicken |
| Audio weg | Mischpult-Verbindung prüfen |

---

## Nach dem Gottesdienst

1. Stream beenden (OBS > Steuerung > Stream stoppen)
2. Lokale Aufnahme stoppen
3. Aufnahme remuxen (OBS > Datei > Aufnahmen remuxen > MKV→MP4)
4. Kamera ausschalten
5. USB-PD trennen
6. Aufnahme auf Server/Cloud sichern
7. YouTube-Stream öffentlich schalten / Thumbnail setzen

---

## Gespeicherte Kamera-Programme (Custom Modes)

Die S5IIX kann bis zu 3 Custom-Programme speichern (C1, C2, C3 auf dem Modus-Rad):

| Custom Mode | Konfiguration | Einsatz |
|---|---|---|
| C1 | 25p, F2.8, Zone-AF, Standard | Prediger-Normalmodus |
| C2 | 25p, F4.0, Gesamtbereich-AF | Chor/Gruppe |
| C3 | 25p, F2.0, Verfolgung-AF | Bewegte Szenen |

**Speichern:** Setup-Menü > Setup 2 > Eigene Programme speichern > Modus wählen > Einstellungen übernehmen

---

## Notfall-Karte (ausdrucken und ans Stativ kleben!)

```
╔══════════════════════════════════════════╗
║ NOTFALL-HILFE KIRCHENSTREAMING           ║
╠══════════════════════════════════════════╣
║ Kein Bild:      HDMI prüfen, Kamera     ║
║                 aus/ein                  ║
║ Kein Fokus:     AF-OFF Touch, dann      ║
║                 erneut AF aktivieren     ║
║ Kein Stream:    OBS > Stream starten     ║
║ Kein Ton:       Mischpult prüfen        ║
║ Kamera dunkel:  USB-PD Kabel prüfen     ║
║                                          ║
║ YouTube Studio: studio.youtube.com       ║
║ Stream-Key:     [hier eintragen]         ║
╚══════════════════════════════════════════╝
```
