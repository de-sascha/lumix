# Samyang AF 35-150mm F2-2.8 — L-Mount

## Technische Daten

| Parameter | Wert |
|---|---|
| Brennweite | 35-150mm |
| Lichtstärke | F2.0 (35mm) bis F2.8 (150mm) |
| Mount | L-Mount (nativ) |
| AF-Motor | STM (Stepping Motor) |
| Gewicht | ca. 1.165g |
| Filterdurchmesser | 82mm |
| Min. Fokusabstand | 0.33m (35mm) / 0.85m (150mm) |
| Bildstabilisierung | Keine (nutzt Kamera-IBIS) |
| **Firmware (aktuell)** | **Ver. 3.6** (16.12.2025) — neueste verfügbare Version (verifiziert via lksamyang.com 2026-05-20) |

## AF-Verhalten auf der S5IIX

### Phase-Hybrid-AF Kompatibilität

- Als natives L-Mount-Objektiv nutzt das Samyang den Phasen-Hybrid-AF der S5IIX
- AF-Performance ist grundsätzlich **gut**, aber nicht auf dem Niveau nativer Panasonic-Objektive
- STM-Motor ist leise genug für Video
- **Fly-by-Wire Fokussierung** (kein mechanischer Fokusring-Anschluss)

### Bekannte Einschränkungen

| Situation | Verhalten | Workaround |
|---|---|---|
| F2.8 @ 150mm in Low-Light | Gelegentliches Hunting | Auf F3.5-4.0 abblenden |
| Schnelle Motivwechsel | Etwas langsamer als native Linsen | AF-Empfindlichkeit auf +1 |
| Breathing | Leichtes Focus Breathing vorhanden | Bei Streaming kaum sichtbar |

### Breathing-Kompensation

Die S5IIX bietet eine Breathing-Kompensation, aber diese funktioniert primär mit **kompatiblen Panasonic-Objektiven**. Für das Samyang ist die Funktion **wahrscheinlich nicht verfügbar/wirksam**.

### Dual I.S. (IBIS + OIS)

**NICHT verfügbar** — Das Samyang hat keinen optischen Stabilisator (OIS). Es nutzt ausschließlich die kamerainterne Bildstabilisierung (IBIS). Dual I.S. 2 funktioniert nur mit kompatiblen Panasonic/Sigma L-Mount-Objektiven mit OIS.

**Für Stativ-Betrieb irrelevant** — IBIS sollte bei Stativ-Nutzung ohnehin ausgeschaltet werden.

## Optimale Einstellungen für Kirchenstreaming

### Empfohlene Brennweiten

| Situation | Brennweite | Blende | ISO (typisch) |
|---|---|---|---|
| Prediger Halbkörper | 85-100mm | F2.8 | 800-1600 |
| Prediger Porträt | 120-150mm | F2.8 | 800-3200 |
| Bühne/Altar Überblick | 35-50mm | F2.8-4.0 | 400-1600 |
| Chor-Gruppe | 50-70mm | F3.5-4.0 | 800-1600 |

### Warum dieses Objektiv ideal ist

- **F2.0-2.8 über gesamten Bereich** = exzellent für Kirchen mit schwacher Beleuchtung
- **35-150mm Zoombereich** = von Weitwinkel bis Porträt-Tele ohne Objektivwechsel
- Bokeh bei F2.0-2.8 gibt professionellen Filmlook
- Keine Objektivwechsel während des Gottesdienstes nötig

### AF-Konfiguration speziell für dieses Objektiv

```
AF-Modus:                Zone (H/V) auf Kanzel
Fokusmodus:              AFC
AF-Empfindlichkeit:      0 (statischer Prediger) / +1 (Chor)
AF-Geschwindigkeit:      Mittel bis Schnell
Fokusring-Steuerung:     NONLINEAR (Individualmenü > Objektiv/Weitere)
```

## Gewicht & Balance auf Stativ

- 1.165g Objektiv + 740g Kameragehäuse = **ca. 1.900g Gesamtgewicht**
- Schwerpunkt liegt deutlich vor der Stativplatte → **Stativplatte am Objektiv-Fuß** (falls vorhanden) oder Arca-Swiss L-Bracket
- Stativ muss mindestens 3-4kg tragen können
- Bei langen Brennweiten (150mm): gutes Fluid-Head empfohlen für ruhige Schwenks

## Firmware-Updates

**Aktueller Stand:** Ver. 3.6 (16. Dezember 2025) — installiert und aktuell.

### Update-Prozess für L-Mount

Anders als bei Sony-FE-Objektiven gibt es für L-Mount **keinen Lens Manager** und **keine Lens Station**. Das Objektiv-Firmware-Update läuft direkt **über die Kamera**:

1. Firmware-Datei von https://www.lksamyang.com/en/support/support-download.php?model=L herunterladen (Filter "L")
2. ZIP entpacken, `.bin`-Datei ins Root-Verzeichnis einer FAT/exFAT-formatierten SD-Karte kopieren
3. Objektiv an die Kamera anschließen, SD-Karte in Slot 1
4. Akku >50 % oder Netzteil
5. Setup-Menü > Sonstige > Firmware-Anz. → die Kamera erkennt die Objektiv-Firmware und bietet das Update an
6. ⚠ Während des Updates Kamera nicht ausschalten und Objektiv nicht entfernen

### Firmware-Historie (L-Mount)

| Version | Datum | Quelle |
|---|---|---|
| **3.6** | 16.12.2025 | Download-Bereich (keine Notice veröffentlicht) |
| 3.5 | unbekannt | (keine Notice veröffentlicht) |
| 3.4 | 17.12.2024 | Notice seq=1740 |
| 2.1 | 02.09.2024 | Notice seq=1686 |
| 1.0 | 04.06.2024 | Launch |

> Hinweis: Lk Samyang veröffentlicht nicht alle L-Mount-Updates auf der Notice-Seite. Für den verlässlichen aktuellen Stand immer den **Download-Bereich mit Filter "L"** prüfen.

### Hinweis zu Firmware-Updates der Sony-FE-Variante

Das Notice vom **07.01.2026** (Stabilität mit Sony α7 V) betrifft **nur die FE-Version** des 35-150mm. Die L-Mount-Variante ist nicht betroffen.

---

## Vergleich mit Kit-Objektiv für Streaming

| Eigenschaft | Samyang 35-150 F2-2.8 | Lumix S 18-40 F4.5-6.3 |
|---|---|---|
| Low-Light | Exzellent (F2.0-2.8) | Schlecht (F4.5-6.3) |
| AF-Speed | Gut | Sehr gut (nativ) |
| Dual I.S. | Nein | Nein (kein OIS) |
| Brennweitenbereich | 35-150mm | 18-40mm |
| Gewicht | 1.165g | 172g |
| Video-Eignung | Sehr gut | Eingeschränkt (lichtschwach) |
| Bokeh | Stark (F2.0-2.8) | Minimal (F4.5-6.3) |
| **Streaming-Empfehlung** | **Hauptobjektiv** | Nur für extreme Weitwinkel-Shots |
