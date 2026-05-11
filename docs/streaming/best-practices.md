# Best Practices — Langzeit-Streaming Kirchengottesdienst

## Vor-Ort-Checkliste (30 Minuten vor Beginn)

### Strom & Kabel
- [ ] USB-PD Netzteil an Kamera angeschlossen (Lade-Symbol sichtbar)
- [ ] Backup-Akku BLK22 voll geladen eingelegt
- [ ] HDMI-Kabel fest an Kamera und DeckLink (Zugentlastung prüfen)
- [ ] LAN-Kabel am OBS-PC eingesteckt
- [ ] Steckdosenleiste mit Überspannungsschutz

### Kamera-Einstellungen
- [ ] Modus: Kreative Filme (M)
- [ ] Systemfrequenz: 50 Hz (PAL)
- [ ] Shutter: 1/50s (fest)
- [ ] Blende: F2.8-4.0 (je nach Licht)
- [ ] ISO: Auto (100-6400)
- [ ] Weißabgleich: Manuell (Kelvin-Wert für diese Kirche)
- [ ] Bildstil: Standard oder Natural
- [ ] AF: AFC, Zone auf Kanzel, FACE/EYE
- [ ] Dauer-AF: MODE 1
- [ ] Sleep Mode: OFF
- [ ] Lüfter: AUTO2
- [ ] Temperaturmanagement: HIGH
- [ ] IBIS: OFF (Stativ)
- [ ] HDMI Info Display: OFF

### OBS & Stream
- [ ] OBS gestartet, DeckLink-Signal sichtbar
- [ ] Encoder: NVENC H.264, CBR 8-12 Mbps
- [ ] Stream-Key aktuell (YouTube/Platform)
- [ ] Lokale Aufnahme aktiviert (MKV)
- [ ] Audio-Signal vorhanden und Pegel korrekt
- [ ] Internet Speed-Test: Upload stabil >20 Mbit

### Test-Run
- [ ] 5-Minuten Test-Stream starten und auf Handy prüfen
- [ ] Bild-/Tonqualität OK
- [ ] Keine Dropped Frames in OBS
- [ ] Kamera-Temperatur stabil

---

## Häufige Probleme & Sofort-Lösungen

### Kamera geht in Standby
**Sofort:** Auslöser halb drücken oder ON/OFF kurz betätigen
**Prävention:** Alle Sleep-Modi auf OFF, HDMI-Verbindung aktiv halten

### Fokus "pumpt" / huntet
**Sofort:** AF per Touch-Button pausieren (AF OFF auf Display tippen)
**Prävention:** Zone-AF statt Gesamtbereich, Empfindlichkeit auf 0

### Bild wird zu dunkel/hell (Licht wechselt)
**Sofort:** Belichtungskorrektur anpassen (±EV)
**Prävention:** Auto-ISO mit manuellem Shutter (1/50s) + manueller Blende

### HDMI-Signal bricht ab
**Sofort:** Kabel überprüfen, Kamera Power-Cycle
**Prävention:** Hochwertige Kabel, Zugentlastung, Kabellänge beachten

### OBS zeigt Dropped Frames
**Sofort:** Bitrate um 2-3 Mbps reduzieren
**Prävention:** Gigabit-LAN, QoS am Router, keine Upload-Last durch andere Geräte

### Bild-Flicker/Banding bei Kunstlicht
**Sofort:** Shutter auf 1/50s oder 1/100s stellen
**Ursache:** Shutter-Speed nicht harmonisch mit 50Hz-Netzfrequenz

---

## Belichtungsstrategie für variable Kirchenbeleuchtung

### Typische Lichtsituationen in einer Kirche

| Situation | Lux (ca.) | Empfohlene Einstellung |
|---|---|---|
| Heller Tag, große Fenster | 500-2000 | F4.0, ISO 400-800 |
| Normal beleuchtet, Kunstlicht | 100-500 | F2.8, ISO 800-1600 |
| Stimmungsvoll, gedimmt | 50-100 | F2.0-2.8, ISO 1600-3200 |
| Kerzenlicht, sehr dunkel | 10-50 | F2.0, ISO 3200-6400 |
| Spotlight auf Prediger | Lokal hell | Spot/Face-Metering verwenden |

### Empfohlener Ansatz: Aperture Priority (A-Modus)

```
Blende:               F2.8 (fest oder leicht geschlossen)
Shutter:              1/50s (fest über Minimum-Shutter-Speed)
ISO:                  Auto (100-6400, Maximum)
Belichtungskorrektur: -0.3 bis -0.7 EV (Highlights schützen)
Messmethode:          Multi/Evaluativ (oder Gesichtspriorität)
```

### Weißabgleich — IMMER MANUELL

**Niemals Auto-Weißabgleich für Streaming!**
- AWB verändert Farben zwischen Einstellungen → irritierend für Zuschauer
- Einmal vor dem Gottesdienst manuell messen (Graukarte oder Kelvin-Wert)
- Typische Werte: 3200K (Halogen), 4000K (LED warmweiß), 5000K (LED neutral)

---

## Dual Native ISO der S5IIX

Die S5IIX hat **Dual Native ISO**:
- **Basis ISO 1: 640** (bester Dynamikumfang, niedrigstes Rauschen)
- **Basis ISO 2: 4000** (höherer Basiswert, aber GLEICH niedriges Rauschen)

### Was bedeutet das für Kirchenstreaming?

- Bei ISO <640: Maximaler Dynamikumfang
- Bei ISO 640-3200: Normaler Anstieg des Rauschens
- Bei ISO 4000: **Zweiter "sauberer" Startpunkt** — Rauschen ist hier GERINGER als bei ISO 3200!
- Bei ISO >4000: Normaler Anstieg ab dem zweiten Basiswert

**Praxis-Tipp:** Wenn Auto-ISO zwischen 2000-5000 wechselt, kann ein Sprung sichtbar sein. Lösung: ISO manuell auf 640 ODER 4000 festlegen (je nach Licht).

---

## Audio-Best-Practices

### Kamera-Audio für Streaming: NICHT verwenden

Das Kamera-Mikrofon ist für Streaming ungeeignet:
- Zu weit entfernt vom Sprecher
- Nimmt Raumhall auf
- Lüftergeräusch möglich

### Empfohlener Audio-Workflow

```
┌────────────┐    XLR    ┌──────────────┐   USB/Audio    ┌─────────┐
│ Kirchen-   │──────────│ Audio        │──────────────│ OBS PC  │
│ Mischpult  │          │ Interface    │              │         │
└────────────┘          └──────────────┘              └─────────┘
```

Oder direkt über HDMI (falls Audio-Embedder vorhanden):
```
┌────────────┐    Analog    ┌──────────────┐   HDMI    ┌──────────┐
│ Kirchen-   │─────────────│ HDMI Audio   │─────────│ DeckLink │
│ Mischpult  │             │ Embedder     │          │          │
└────────────┘             └──────────────┘          └──────────┘
```

### Tonpegel-Einstellung (falls Kamera-Audio als Backup)

Aus dem Praxisbuch (Sänger):
- **Videomenü > Audio 1 > Tonpegel-Anzeige: ON**
- **Tonpegel anpassen:** Maximum im grünen bis unteren gelben Bereich
- **Niemals in den roten Bereich** → Übersteuerung/Verzerrung
- **Tonverstärkungspegel:** Standard (LOW nur bei sehr lauter Umgebung)
- **Windgeräuschunterdr.:** STANDARD (HIGH bei Outdoor, OFF bei Indoor-Kirche)

---

## Langzeit-Zuverlässigkeit

### Getestete maximale Dauerbetriebszeiten

| Konfiguration | Erwartete Laufzeit |
|---|---|
| HDMI-Out + USB-PD + AUTO2 Lüfter + kein internes Rec | **Unbegrenzt** (3h+ bestätigt) |
| HDMI-Out + USB-PD + FHD intern | 3-5h+ (Wärme-abhängig) |
| HDMI-Out + USB-PD + 4K intern | 1.5-3h (abhängig von Umgebungstemperatur) |
| Nur HDMI-Out + Akku (kein USB-PD) | 70-90 Min. (1x BLK22) |

### Monatliche Wartung

- SD-Karte formatieren (falls intern aufgenommen wird)
- Firmware-Update prüfen (Panasonic Support-Seite)
- Akku-Zustand prüfen (wenn BLK22 nicht mehr auf 100% kommt → ersetzen)
- HDMI-Kabel und USB-C-Kabel auf Beschädigungen prüfen
- Sensor reinigen (bei sichtbaren Flecken im Bild)
- OBS auf Updates prüfen
- Blackmagic Desktop Video auf Updates prüfen

---

## Zusammenfassung: Goldene Regeln

1. **HDMI-Output ohne interne Aufnahme** = maximale Thermik-Reserve
2. **USB-PD + Akku** = unbegrenzte Laufzeit mit Failover
3. **PAL 25p + 1/50s** = flickerfreies Bild in EU-Kirchen
4. **Manueller Weißabgleich** = konsistente Farben über den gesamten Stream
5. **Zone-AF mit Gesichtserkennung** = zuverlässiger Fokus auf den Prediger
6. **Standard/Natural Bildstil** = stream-ready ohne LUT
7. **Lüfter AUTO2 + Temp-Management HIGH** = thermische Sicherheit
8. **CBR 8-12 Mbps über LAN** = stabiler, qualitativ hochwertiger Stream
9. **Test-Run vor jedem Gottesdienst** = Probleme frühzeitig erkennen
10. **Lokale Aufnahme in OBS als Backup** = immer eine Sicherheitskopie
