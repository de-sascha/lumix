# Kapitel 9 — Samyang AF 35-150mm F2-2.8 (Hauptobjektiv)

> Teil III, Kapitel 9 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [8. HDMI-Ausgabe](../camera/hdmi-output.md). Nächstes Kapitel: [10. Lumix S 18-40mm Kit](lumix-18-40.md).

## Worum geht es hier?

Das Samyang AF 35-150mm F2-2.8 ist unser **Hauptobjektiv** für Hosanna-Streams. Dieses Kapitel erklärt, warum genau dieses Objektiv für unseren Einsatz ideal ist, wie sich der Autofokus damit verhält, welche Brennweite zu welcher Szene passt — und wie man die Firmware des Objektivs aktualisiert (das geht direkt über die Kamera).

> **Vorab in einem Satz:** Lichtstark genug für jede Kirche, weiter Zoombereich (von Halbtotale bis Porträt-Tele), keine Objektivwechsel mehr während des Gottesdienstes nötig.

---

## 9.1 Begriffe vorab — was die Spezifikationen bedeuten

Bevor die Tabelle Sinn ergibt, kurz die wichtigsten Begriffe in Alltagssprache:

- **Brennweite** (in Millimetern, mm) — Bestimmt, wie „nah dran" das Bild aussieht. Kleine Zahl = weiter Blickwinkel (zeigt mehr); große Zahl = Tele-Effekt (zeigt weniger, dafür größer). Ein Zoom-Objektiv deckt einen Bereich ab, hier 35–150 mm.
- **Lichtstärke (Blende, F-Wert)** — Wie viel Licht das Objektiv durchlässt. **Kleinere Zahl = mehr Licht = besser für dunkle Räume**. F2.0 ist sehr lichtstark, F6.3 sehr lichtschwach. F2-2.8 heißt: bei kürzester Brennweite (35 mm) maximal F2.0 möglich, bei längster (150 mm) maximal F2.8 — bleibt also über den ganzen Zoombereich sehr lichtstark.
- **Mount** — Der mechanische Anschluss an der Kamera. „L-Mount" passt direkt an die S5IIX (kein Adapter nötig).
- **AF-Motor (STM)** — Wie das Objektiv intern fokussiert. STM = Stepping Motor, leise und feinfühlig — wichtig für Video.
- **Bildstabilisierung (OIS) / IBIS** — OIS = Optical Image Stabilizer im Objektiv, gleicht Verwacklungen aus. IBIS = sitzt in der Kamera. Das Samyang hat **kein OIS** und nutzt nur IBIS — auf dem Stativ ohnehin kein Thema.
- **Filterdurchmesser** — Welche Schraub-Filter (z. B. ND-Filter) auf das Objektiv passen.

## 9.2 Technische Daten

| Parameter | Wert |
|---|---|
| Brennweite | 35–150 mm |
| Lichtstärke | F2.0 (bei 35 mm) bis F2.8 (bei 150 mm) |
| Mount | L-Mount (nativ, kein Adapter) |
| AF-Motor | STM (Stepping Motor) |
| Gewicht | ca. 1.165 g |
| Filterdurchmesser | 82 mm |
| Min. Fokusabstand | 0,33 m bei 35 mm / 0,85 m bei 150 mm |
| Bildstabilisierung | Keine (nutzt IBIS der Kamera) |
| **Firmware (aktuell)** | **Ver. 3.6** (16.12.2025) — neueste Version (verifiziert via lksamyang.com 2026-05-20) |

---

## 9.3 Wie der Autofokus auf der S5IIX arbeitet

### Wichtigste Zusammenfassung

Das Samyang ist ein **natives L-Mount-Objektiv** — also kein per Adapter angeflanschtes Fremdsystem. Es nutzt den **Phasen-Hybrid-AF** der S5IIX (siehe [Kapitel 7.1](../camera/af-settings.md#71-wie-der-af-in-der-s5iix-funktioniert-in-kürze)) direkt. AF-Performance ist **gut**, aber **nicht ganz** auf dem Niveau echter Panasonic-Objektive (die wir nicht in dieser Brennweite/Lichtstärke haben — also Kompromiss bewusst eingegangen).

Zwei kleine Eigenheiten:

- **STM-Motor**: leise genug für Video, kein hörbares Rattern.
- **Fly-by-Wire-Fokussierung**: der Fokusring hat keinen mechanischen Anschlag — er steuert nur elektronisch. Im Video meistens irrelevant; relevant nur bei manuellem Fokus mit präzisen Marken.

### Bekannte Einschränkungen und Workarounds

| Situation | Verhalten | Workaround |
|---|---|---|
| F2.8 bei 150 mm in Low-Light | Gelegentliches Hunting (AF pumpt) | Auf F3.5–4.0 abblenden — mehr Schärfentiefe stabilisiert den AF |
| Schnelle Motivwechsel | Etwas langsamer als native Linsen | AF-Empfindlichkeit auf +1 erhöhen (siehe [Kapitel 7.6](../camera/af-settings.md#76-feineinstellungen--der-af-wird-trotzdem-unruhig)) |
| Focus Breathing | Leichte Veränderung des Bildausschnitts beim Fokuswechsel | Bei Streaming kaum sichtbar |

> **Was ist „Focus Breathing"?** Wenn beim Fokussieren der Bildausschnitt ganz leicht „atmet" — wie ein Mini-Zoom in/aus. Beim Filmen sichtbar als kurzes Wackeln. Beim Streaming, wo der Fokus selten umspringt, fällt es kaum auf.

### Was nicht funktioniert: Breathing-Kompensation und Dual I.S. 2

Beide Funktionen der S5IIX brauchen ein **kompatibles Panasonic-Objektiv**.

- **Breathing-Kompensation:** Mit dem Samyang wahrscheinlich nicht wirksam.
- **Dual I.S. 2** (Stabilisierung im Objektiv + Kamera kombiniert): Funktioniert hier nicht, weil das Samyang gar kein OIS hat. Auf dem Stativ ohnehin egal — IBIS gehört dort sowieso aus (siehe [Kapitel 5.3](../camera/thermal-management.md#53-wärme-reduktion-was-hilft-sonst-noch)).

---

## 9.4 Warum dieses Objektiv für Hosanna ideal ist

Drei Gründe:

1. **F2.0–2.8 über den ganzen Zoombereich** — auch bei 150 mm noch F2.8. Damit kommt man in fast jeder Kirchenbeleuchtung mit moderatem ISO aus, ohne dass das Bild rauscht.
2. **35–150 mm = von Halbtotale bis Porträt-Tele** — ein Objektiv für alle Hosanna-Szenen: Kanzel-Halbkörper bei ~85 mm, Prediger-Porträt bei 120–150 mm, Bühnen-Übersicht bei 35 mm. **Keine Objektivwechsel während des Gottesdienstes nötig.**
3. **Bokeh** (= unscharfer Hintergrund) bei F2.0–2.8 sieht professionell aus — verleiht dem Stream einen „cineastischen" Charakter, der mit dem lichtschwachen Kit-Objektiv nicht möglich ist.

---

## 9.5 Welche Brennweite für welche Szene?

Praktische Empfehlungen zum Nachschlagen während des Setups. ISO-Werte sind grobe Anhaltspunkte für typische Hosanna-Beleuchtung — die genaue Belichtungsstrategie liegt in [Kapitel 15 — Best Practices](../streaming/best-practices.md).

| Situation | Brennweite | Blende | ISO (typisch) |
|---|---|---|---|
| Bühne / Altar Übersicht | 35–50 mm | F2.8–4.0 | 400–1600 |
| Chor-Gruppe | 50–70 mm | F3.5–4.0 | 800–1600 |
| Prediger Halbkörper | 85–100 mm | F2.8 | 800–1600 |
| Prediger Porträt-Closeup | 120–150 mm | F2.8 | 800–3200 |

---

## 9.6 Empfohlene AF-Konfiguration speziell für dieses Objektiv

Basis-Profil aus [Kapitel 7.4 — Szene 1](../camera/af-settings.md#szene-1--statischer-prediger-an-der-kanzel-standard-profil) plus zwei Samyang-spezifische Anpassungen:

```
AF-Modus:                Zone (H/V) auf Kanzel
Fokusmodus:              AFC
AF-Empfindlichkeit:      0 (statischer Prediger) / +1 (Chor)
AF-Geschwindigkeit:      Mittel bis Schnell
Fokusring-Steuerung:     NONLINEAR
                         (Individualmenü → Objektiv/Weitere)
```

**Was bedeutet „Fokusring-Steuerung NONLINEAR"?** Bei Fly-by-Wire-Objektiven kann man wählen, ob eine schnelle Drehung des Fokusrings den Fokus weiter springen lässt als eine langsame (NONLINEAR) oder ob die Fokus-Bewegung pro Drehgrad immer gleich ist (LINEAR). Für unseren AF-betriebenen Streaming-Einsatz reicht NONLINEAR — feinjustieren am Ring kommt selten vor.

---

## 9.7 Gewicht und Stativ-Balance

Mit 1.165 g ist das Samyang ein **schweres Objektiv**. Zusammen mit dem Kameragehäuse (740 g) ergibt das **ca. 1.900 g Gesamtgewicht** — das hat zwei Konsequenzen:

- **Schwerpunkt liegt deutlich vor der Stativplatte.** Das Setup kippt am Stativ leicht nach vorne. Lösung: entweder das Objektiv selbst hat eine Stativfuß (manche Versionen) oder ein **Arca-Swiss L-Bracket** an der Kamera, dann den Schwerpunkt mittig auf die Stativplatte legen.
- **Stativ braucht Tragkraft.** Mindestens 3–4 kg Tragkraft — Billig-Reisestative sind hier überfordert, das Bild kann zittern.

Für ruhige Schwenks am langen Ende (150 mm) hilft ein **Fluid-Head** (Video-Stativkopf mit gedämpfter Bewegung).

---

## 9.8 Firmware-Update für das Objektiv

### Aktueller Stand

**Ver. 3.6** (16. Dezember 2025) — installiert und neueste verfügbare Version.

### Wie funktioniert das Update?

Anders als bei Sony-FE-Objektiven gibt es für L-Mount **keinen separaten „Lens Manager"** und **keine Lens Station**. Das Objektiv-Update läuft **direkt über die Kamera** — also genauso wie ein Kamera-Firmware-Update, mit dem Unterschied, dass die Firmware-Datei im Hintergrund das Objektiv aktualisiert.

1. Firmware-Datei von https://www.lksamyang.com/en/support/support-download.php?model=L herunterladen (Filter „L" für L-Mount).
2. ZIP entpacken, die `.bin`-Datei auf eine **frisch in der Kamera formatierte SD-Karte** kopieren — ins Wurzelverzeichnis (nicht in einen Unterordner).
3. Objektiv an die Kamera anschließen, SD-Karte in Slot 1 stecken.
4. Akku > 50 % oder USB-PD-Netzteil anschließen.
5. **Setup-Menü → Sonstige → Firmware-Anz.** — die Kamera erkennt die Objektiv-Firmware und bietet das Update an.
6. ⚠ **Während des Updates** Kamera nicht ausschalten und Objektiv **nicht abnehmen**.

### Firmware-Historie (L-Mount-Variante)

| Version | Datum | Quelle |
|---|---|---|
| **3.6** | 16.12.2025 | Download-Bereich (keine Notice veröffentlicht) |
| 3.5 | unbekannt | (keine Notice veröffentlicht) |
| 3.4 | 17.12.2024 | Notice seq=1740 |
| 2.1 | 02.09.2024 | Notice seq=1686 |
| 1.0 | 04.06.2024 | Launch |

> **Hinweis:** Lk Samyang veröffentlicht nicht alle L-Mount-Updates auf der Notice-Seite. Für den verlässlichen aktuellen Stand immer den **Download-Bereich mit Filter „L"** prüfen.

### Hinweis zu Sony-FE-Updates (uns betrifft das nicht)

Das Notice vom **07.01.2026** (Stabilität mit Sony α7 V) betrifft **nur die FE-Version** des Samyang 35-150. Die L-Mount-Variante, die wir nutzen, ist nicht betroffen — diese Notice kann ignoriert werden.

---

## 9.9 Direkter Vergleich mit dem Kit-Objektiv

Damit klar ist, warum das Samyang die erste Wahl ist und der Lumix-Kit nur Backup. Details zum Kit in [Kapitel 10](lumix-18-40.md).

| Eigenschaft | Samyang 35-150 F2-2.8 | Lumix S 18-40 F4.5-6.3 |
|---|---|---|
| Low-Light | Exzellent (F2.0–2.8) | Schlecht (F4.5–6.3) |
| AF-Geschwindigkeit | Gut | Sehr gut (nativ Panasonic) |
| Dual I.S. 2 | Nein | Nein (kein OIS) |
| Brennweitenbereich | 35–150 mm | 18–40 mm |
| Gewicht | 1.165 g | 172 g |
| Video-Eignung | Sehr gut | Eingeschränkt (lichtschwach) |
| Bokeh / Hintergrund-Unschärfe | Stark (F2.0–2.8) | Minimal (F4.5–6.3) |
| **Streaming-Empfehlung** | **Hauptobjektiv** | Nur für extreme Weitwinkel-Aufnahmen |
