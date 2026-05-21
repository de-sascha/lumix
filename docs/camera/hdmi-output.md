# Kapitel 8 — HDMI-Ausgabe

> Teil II, Kapitel 8 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [7. Autofokus](af-settings.md). Nächstes: [Teil III — Objektive](../lenses/samyang-35-150.md).

## Worum geht es hier?

Das Bild der S5IIX muss in den Streaming-PC kommen. Wir machen das per **HDMI-Kabel**: Kamera → HDMI → Capture-Karte (Blackmagic DeckLink) → OBS Studio.

Damit das ohne Kompromisse funktioniert, müssen drei Dinge stimmen:

1. **Clean HDMI** — die Kamera darf keine Menü-Overlays (ISO, Blende, Fokus-Rahmen) ins Bild einblenden.
2. **Passende Auflösung und Farbtiefe** — sodass die Capture-Karte das Signal sauber annehmen kann.
3. **Das Kabel hält den ganzen Gottesdienst** — physische Sicherung am Kamera-Rig.

Dieses Kapitel arbeitet diese drei Punkte ab.

---

## 8.1 Anschluss und Grundkonfiguration

### Welcher Anschluss?

Die S5IIX hat einen **Full-Size HDMI-Anschluss (Typ A)** — der „normale", große HDMI-Stecker. Das ist robuster als die Mini- oder Micro-HDMI-Anschlüsse vieler Konkurrenzkameras.

Verbunden wird er mit dem HDMI-Eingang der **Blackmagic DeckLink Mini Recorder 4K**. Details zur DeckLink-Seite siehe [Kapitel 12](../obs/blackmagic-setup.md).

### Menü-Pfad

`Setup-Menü → EIN/AUS → HDMI`

### Empfohlene Einstellungen für Streaming

| Einstellung | Unser Wert | Warum |
|---|---|---|
| HDMI Mode Output | **Auto** oder **4K** | DeckLink unterstützt bis 4K. „Auto" handelt das beste Format selbst aus. |
| **Info Display HDMI** | **OFF** | Ohne Overlays — siehe Abschnitt 8.2! |
| HDMI Recording Control | OFF | Würde die Kamera versuchen, der DeckLink Aufnahme-Trigger zu senden. Brauchen wir nicht. |
| Down Convert | OFF (bei 4K-Output) / ON (bei 1080p) | Je nachdem, ob 4K oder 1080p ans OBS gehen sollen. |

---

## 8.2 Clean HDMI: die wichtigste Einstellung

`Info Display HDMI` muss **OFF** stehen. Sonst sendet die Kamera ihr komplettes Bedien-Overlay mit ins HDMI-Signal — Blende, ISO, Fokus-Rahmen, Histogramm, Symbole. Alles davon wäre dann live im Stream zu sehen.

> **Diese Einstellung ist die wichtigste in diesem Kapitel.** Wenn sie falsch steht, ist der Stream unbrauchbar — egal wie gut alles andere konfiguriert ist.

**Test, ob es korrekt steht:** In OBS die Kamera-Quelle anzeigen lassen und prüfen, ob das Bild „nackt" ist. Keine Symbole, kein Rahmen, nur das reine Live-Bild.

---

## 8.3 4K oder 1080p ausgeben?

Das ist eine echte Designentscheidung mit Vor- und Nachteilen auf beiden Seiten.

### Variante A — 4K (3840×2160) an die DeckLink

**Vorteile:**
- **Digital reinzoomen in OBS, ohne Qualitätsverlust.** Selbst bei 2× Zoom hat man immer noch 1080p-natives Bild. Sehr wertvoll für Einzelkamera-Setups: vom Gesamtbild auf Prediger-Closeup zoomen, ohne ein zweites Objektiv zu brauchen.
- Höhere Bildqualität als Basis für den finalen 1080p-Downscale.

**Nachteile:**
- Etwas mehr Wärme in der Kamera.
- OBS muss von 4K auf 1080p herunterskalieren — leichte GPU-Mehrlast.
- DeckLink muss 4K verarbeiten (sie kann es, aber es ist mehr Datenrate).

### Variante B — 1080p (1920×1080) an die DeckLink

**Vorteile:**
- Weniger Wärme in der Kamera.
- Geringere System-Last in OBS, einfachere Pipeline.

**Nachteile:**
- **Kein digitales Reinzoomen.** Der Bildausschnitt ist fix.

### Empfehlung für Hosanna

**4K ausgeben → in OBS auf 1080p für den Stream skalieren.**

Begründung: Wir haben nur **eine** S5IIX. Die Möglichkeit, während des Gottesdienstes vom Weitwinkel-Gesamtbild ins Detail zu zoomen (Prediger-Closeup, Sänger), ist mehr wert als die kleine Wärme-Ersparnis von 1080p-Output.

---

## 8.4 Farbtiefe und Farbraum

Für Streaming verwenden wir den Farbraum **Rec.709** — der Standard, in dem YouTube und Facebook Videos erwarten. Dazu eine Farbtiefe von **4:2:2 10-Bit**.

| Parameter | Einstellung |
|---|---|
| Farbtiefe HDMI | 4:2:2 10-Bit |
| Farbraum / Gamma | Rec.709 (kommt automatisch über Bildstil **Standard** oder **Natural**) |
| Photo Style | Standard oder Natural |

### Was die Begriffe bedeuten

- **4:2:2 / 4:2:0** — wie viel Farbinformation pro Pixel übertragen wird. 4:2:2 hat mehr Farbdetails, ist aber für Streaming-Encoder (NVENC AV1) nur dann ein Vorteil, wenn der Encoder auch 4:2:2 verarbeitet. Bei uns reicht **4:2:0 10-Bit** völlig — die DeckLink unterstützt aber 4:2:2, also können wir es einfach so lassen.
- **10-Bit** — feinere Farbabstufungen als 8-Bit. Vorteil: weniger sichtbares **Banding** (Streifen) bei sanften Farbverläufen wie blauer Himmel oder Hauttöne.
- **Rec.709** — der Farbraum-Standard für HD-Fernsehen und Streaming. Die meisten Endgeräte erwarten ihn. Solange wir den Bildstil „Standard" oder „Natural" nutzen, kommt das automatisch korrekt heraus.

### KEIN V-Log über HDMI für Live-Streaming

V-Log ist ein flaches Kamera-Profil, das für die Nachbearbeitung gedacht ist und vor der Anzeige eine **LUT** (Look-Up-Table) braucht. In OBS einzubauen ist Bastelei und bringt für Live-Stream nichts. Mehr dazu in [Kapitel 6 — Bildstil](video-settings.md#bildstil-photo-style).

---

## 8.5 RAW-Output (für später, falls relevant)

Die S5IIX kann über HDMI auch **RAW-Daten** ausgeben — ein unkomprimiertes, direkt vom Sensor stammendes Signal. Brauchen wir für Streaming nicht; ist nur relevant, wenn man zu einem **externen Recorder** mit RAW-Unterstützung geht (Atomos Ninja V/V+, Blackmagic Video Assist 12G HDR).

| Parameter | Einstellung (nur falls genutzt) |
|---|---|
| RAW-Datenausgabe über HDMI | ON |
| Kompatibler Recorder | Atomos Ninja V/V+, BM Video Assist 5"/7" 12G HDR |
| Speicherformat | ProRes RAW oder Blackmagic RAW |

**Für unser Hosanna-Setup: OFF.** Die DeckLink ist keine RAW-Capture, also bringt uns das nichts.

---

## 8.6 HDMI-Kabel und mechanische Sicherung

### Welches Kabel?

| Anforderung | Empfohlener Kabeltyp |
|---|---|
| 4K 25p 4:2:2 10-Bit | HDMI 2.0, „High Speed" (18 Gbit/s) |
| Bis 5 m Länge | Standardkabel reicht |
| 5–15 m Länge | **Aktives** HDMI-Kabel oder Glasfaser-HDMI |
| Kabelverriegelung | Empfohlen — siehe unten |

### Wieso das wichtig ist

Der HDMI-Stecker an der Kamera ist mechanisch nicht besonders robust — bei Zug oder Hebelwirkung kann er Wackelkontakte bekommen oder im schlimmsten Fall den Anschluss beschädigen. Im Live-Stream merkt man das als Bild-Aussetzer.

### Sicherung: Kabel-Clamp am Cage oder Stativ

- Eine **HDMI Cable Clamp** klemmt das Kabel direkt am Kamera-Cage oder an der Stativplatte fest.
- Damit wirkt jeder Zug am Kabel auf den Cage, **nicht** auf den HDMI-Anschluss der Kamera.
- Beispiel: SmallRig HDMI Cable Clamp für die S5II/S5IIX.

→ Vor jedem Stream prüfen: sitzt das Kabel beidseitig fest, ist die Clamp wirklich angezogen?

---

## 8.7 Probleme und Lösungen

| Problem | Wahrscheinliche Ursache | Lösung |
|---|---|---|
| Kein Signal auf der DeckLink | DeckLink steht auf SDI statt HDMI | Im Blackmagic Desktop Video Setup auf **HDMI** umstellen (siehe [Kapitel 12](../obs/blackmagic-setup.md)) |
| Bild zeigt Kamera-Overlays | `Info Display HDMI` steht auf ON | Auf **OFF** setzen |
| „Falsche Auflösung" / kein Bild | DeckLink-Format und Kamera-Output passen nicht zusammen | DeckLink auf **Auto-Detect** stellen oder beide manuell auf 2160p25 / 1080p25 |
| Kein Audio in OBS | Audio-Input der DeckLink falsch | Im Desktop Video auf **Embedded** (HDMI-eingebettetes Audio) |
| Schwarzes Bild nach längerer Pause | Kamera ist in Standby gegangen | Spar-Modi prüfen — siehe [Kapitel 4](power-management.md) |
| Sporadische Signal-Aussetzer | Kabel zu lang oder beschädigt | Bei > 5 m: aktives Kabel verwenden; Kabel testweise tauschen |
