# Kapitel 10 — Panasonic Lumix S 18-40mm F4.5-6.3 (Kit-Objektiv)

> Teil III, Kapitel 10 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [9. Samyang AF 35-150mm](samyang-35-150.md). Nächstes Kapitel: [Teil IV — OBS Studio und Encoder](../obs/encoder-settings.md).

## Worum geht es hier?

Das Lumix S 18-40mm ist das **Kit-Objektiv**, das mit der S5IIX-Kamera mitgeliefert wurde. Es ist klein, leicht, **nativ von Panasonic** und hat einen exzellenten Autofokus — aber **lichtschwach** (F4.5–6.3) und auf einen Weitwinkel-Bereich beschränkt. Für Hosanna ist es **nicht das Hauptobjektiv** — das ist das [Samyang 35-150](samyang-35-150.md). Trotzdem hat es seine Einsatzfälle.

Dieses Kapitel erklärt, **warum** es nicht das Hauptobjektiv ist (Lichtstärke-Problem im Detail) und **wann** es trotzdem sinnvoll ist (extrem weite Aufnahmen, als Backup, als Zweitkamera-Objektiv).

> **Vorab in einem Satz:** Tolles Reise-Objektiv, schlechte Wahl für eine Kirche mit Kunstlicht — das Samyang ist hier 4× lichtstärker und damit klar überlegen.

---

## 10.1 Technische Daten

| Parameter | Wert |
|---|---|
| Brennweite | 18–40 mm |
| Lichtstärke | F4.5 (bei 18 mm) bis F6.3 (bei 40 mm) |
| Mount | L-Mount (nativ Panasonic) |
| AF-Motor | STM (Stepping Motor) |
| Gewicht | ca. 172 g |
| Filterdurchmesser | 62 mm |
| Bildstabilisierung | Nein (nutzt IBIS der Kamera) |
| Dual I.S. 2 | Nein (kein OIS im Objektiv) |

> **Begriffe nicht klar?** Eine kurze Erklärung von Brennweite, Blende, Mount, AF-Motor und IBIS findet sich in [Kapitel 9.1](samyang-35-150.md#91-begriffe-vorab--was-die-spezifikationen-bedeuten).

---

## 10.2 Was es richtig gut kann: Autofokus

Als **natives Panasonic-Objektiv** redet das 18-40 in der gleichen „Sprache" wie die S5IIX-Kamera. Konsequenz: der Autofokus ist hier sogar **besser** als beim Samyang.

| Aspekt | Bewertung |
|---|---|
| AF-Geschwindigkeit | Sehr gut (nativ) |
| AF-Genauigkeit | Sehr gut |
| AF-Geräusch | Praktisch lautlos |
| AF-Hunting bei Video | Minimal |
| Tracking | Zuverlässig |

**Außerdem:** Die **Breathing-Kompensation** der S5IIX (sanftes Ausgleichen des Bildausschnitts beim Fokuswechsel) funktioniert mit nativen Panasonic-Objektiven — also auch hier.

---

## 10.3 Das große Problem: Lichtstärke

In der Kirche ist das Licht meist gedämpft (50–200 Lux Raumbeleuchtung). Damit hat das 18-40 ein grundlegendes Problem.

### Worum es geht

Bei einer festen Verschlusszeit (in PAL: 1/50 s, siehe [Kapitel 6 — 180°-Regel](../camera/video-settings.md#bildrate--shutter-speed-180-regel)) hat man nur zwei Stellschrauben für die Helligkeit: **Blende** (wieviel Licht durchs Objektiv kommt) und **ISO** (wie stark das Sensorsignal verstärkt wird). Wenn die Blende fest „nur F4.5 bis F6.3" lässt — also wenig Licht — muss man die ISO entsprechend hochdrehen. Hohe ISO = mehr Bildrauschen.

### Konkret bei diesem Objektiv

| Brennweite | Maximal verfügbare Blende | ISO nötig bei 1/50 s in typischer Kirche |
|---|---|---|
| 18 mm | F4.5 | ISO 3200–6400 |
| 24 mm | F5.0 | ISO 3200–8000 |
| 35 mm | F5.6 | ISO 4000–8000 |
| 40 mm | F6.3 | ISO 5000–12800 |

Zum Vergleich: Das Samyang braucht in der gleichen Szene **ISO 800–1600** — das sind 2 bis 3 ganze „Blendenstufen" Unterschied (= 4–8× mehr Licht). Das ist im Bild deutlich sichtbar als weniger Rauschen und besserer Dynamikumfang.

### Bonus-Nachteil: kein Bokeh

Bei F4.5–6.3 ist die **Schärfentiefe** (= wie viel des Bildes scharf ist) sehr groß. Hintergrund und Vordergrund sind beide scharf. Das wirkt **dokumentarisch**, nicht **cineastisch** — es fehlt der typische „professionelle" Look mit unscharfem Hintergrund, den das Samyang bei F2.0–2.8 mühelos liefert.

---

## 10.4 Das andere Problem: Brennweitenbereich

18–40 mm ist ein **Ultraweitwinkel- bis Normal-Bereich**. Übersetzt:

- Bei 18 mm sieht man **sehr viel** — fast den ganzen Kirchenraum aus mittlerer Distanz.
- Bei 40 mm hat man eine „natürliche" Perspektive (wie das menschliche Auge ungefähr).
- Es geht nicht ins Tele. **Prediger-Porträts oder Closeups sind nicht möglich** ohne körperlich nah ranzugehen — was während eines Streams keine Option ist.

---

## 10.5 Wann macht das 18-40 trotzdem Sinn?

Es gibt drei Einsatzfälle, in denen das Kit-Objektiv brauchbar oder sogar besser ist als das Samyang:

| Einsatz | Eignung | Anmerkung |
|---|---|---|
| **Gesamtansicht des Kirchenraums** | Gut | Mit 18 mm zeigt man *alles* — Bühne, Gemeinde, Decke. So weit kommt das Samyang nicht (35 mm ist schon enger). |
| **Establishing Shot** (Eingang, Gebäude von außen) | Gut | Klassischer Einsatz für Ultraweitwinkel. |
| **Zweite Kamera (statisch, Weitwinkel-Total)** | Gut | Wenn irgendwann eine zweite S5IIX dazukommt: das 18-40 daraufschrauben, statisch laufen lassen, in OBS als zusätzliche Quelle. |
| Prediger-Closeup | **Nicht geeignet** | Brennweite zu kurz, Lichtstärke zu schwach. |
| Chor-Aufnahme aus Distanz | Mittelmäßig | Distanz + lichtschwach = hohe ISO und kleines Motiv. |

---

## 10.6 Empfohlene Einstellungen — falls doch eingesetzt

```
Modus:                       Kreative Filme (M)
Blende:                      Weit offen (F4.5–6.3, je nach Brennweite)
ISO:                         Auto ISO (Bereich 100–12800)
Verschlusszeit:              1/50 s (fest, PAL)
AF-Modus:                    AF-Gesamtbereich
                             (bei Weitwinkel reicht das, kein Zone-AF nötig)
AF-Erkennungseinstellung:    ON
Bildstil:                    Standard
IBIS:                        AUS (auf Stativ)
```

**Warum AF-Gesamtbereich?** Weil die Schärfentiefe bei F4.5–6.3 ohnehin so groß ist, dass sehr viel im Bild gleichzeitig scharf ist (siehe [Kapitel 7.4 — Szene 3](../camera/af-settings.md#szene-3--weitwinkel-gesamtansicht-mit-lumix-18-40)). Da muss der AF nichts „präzise treffen" — er muss nur grob sehen, dass irgendetwas in der Szene scharf ist.

---

## 10.7 Fazit

- **Hauptobjektiv für Hosanna: das [Samyang 35-150 F2-2.8](samyang-35-150.md).** Lichtstark, flexibel, professioneller Look.
- Das Lumix-Kit ist **kein Ersatz für das Samyang** — es deckt einen anderen Bereich ab und ist deutlich lichtschwächer.
- **Sinnvolle Einsätze:** Ultraweitwinkel-Totale, Außen-Aufnahmen, Backup, Zweitkamera-Objektiv.
- **Unbedingt behalten** trotzdem: kleines Gewicht, exzellenter AF, native Panasonic-Sprache. Im richtigen Moment (sehr weite Aufnahme, Reise, schnelle Schnappschüsse) bleibt es ein gutes Objektiv.
