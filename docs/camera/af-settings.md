# Kapitel 7 — Autofokus

> Teil II, Kapitel 7 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [6. Videoeinstellungen](video-settings.md). Nächstes Kapitel: [8. HDMI-Ausgabe](hdmi-output.md).

## Worum geht es hier?

Der **Autofokus (AF)** stellt das Bild automatisch scharf. In der Kirche muss er zwei Eigenschaften gleichzeitig haben:

1. **Ruhig.** Er darf nicht hin- und herpumpen („Hunting") — das wirkt im Stream unprofessionell und ist ablenkend.
2. **Aufmerksam genug**, um dem Prediger zu folgen, wenn er sich bewegt oder leicht zur Seite tritt.

Dieses Kapitel erklärt, was die S5IIX an Autofokus-Werkzeugen anbietet, und welche Kombination für unsere Hosanna-Streams die richtige ist. Am Ende gibt es fertige Einstellungs-Profile für drei typische Szenen.

> **Vorab-Hinweis:** Es gibt sehr viele Knöpfe. Für den Anfang reicht das Profil **„Statischer Prediger an der Kanzel"** (Abschnitt 7.4). Den Rest kann man später dazulernen.

---

## 7.1 Wie der AF in der S5IIX funktioniert (in Kürze)

Die S5IIX ist Panasonics erste Kamera mit **Phasen-Hybrid-AF**. Das bedeutet, sie kombiniert zwei Techniken:

- **Phasen-AF** — schnell, weiß sofort grob, wo die Schärfe-Ebene liegt. **779 Messpunkte** über die gesamte Sensorfläche.
- **Kontrast-AF** — langsamer, dafür präzise im Feinschliff. **315 Felder**.

Die Kamera nutzt zuerst Phasen-AF zur groben Vorfokussierung, dann Kontrast-AF für den Feinschliff. Für uns als Anwender heißt das: schneller und stabiler AF als bei älteren Panasonic-Modellen, ohne dass man irgendwas konfigurieren müsste.

---

## 7.2 AFC vs. AFS — der wichtigste Unterschied

Bevor man irgendwelche AF-Modi wählt, gibt es eine grundlegendere Entscheidung: **wann** soll die Kamera fokussieren?

| Fokusmodus | Bedeutung | Wann nutzen? |
|---|---|---|
| **AFS** (Single) | Einmal scharfstellen, dann den Fokus festhalten. | Wenn das Motiv sich nicht bewegt (Architektur, statisches Foto). |
| **AFC** (Continuous) | Dauerhaft nachfokussieren, solange Aufnahme läuft. | **Für Video/Streaming praktisch immer.** |
| MF | Manueller Fokus — die Kamera fokussiert gar nicht. | Nur in Spezialfällen. |

**Für unseren Streaming-Einsatz: immer AFC.** So folgt die Kamera dem Prediger, falls er ein paar Schritte zur Seite geht.

---

## 7.3 AF-Modi: wo schaut die Kamera hin?

Während der Fokusmodus (AFC/AFS) bestimmt, **wann** fokussiert wird, regelt der AF-Modus, **welcher Bildbereich** dabei beachtet wird. Die wichtigsten:

| AF-Modus | Symbol | Was macht er? | Wann sinnvoll? |
|---|---|---|---|
| **Verfolgung** | ₊₅ | Markiert ein Motiv und folgt ihm im ganzen Bild. | Bewegte Motive (Chor, der sich umherbewegt). |
| **AF-Gesamtbereich** | ▦ | Sucht im ganzen Bild nach passenden Motiven (z. B. Gesichtern). | Spontane Situationen, mehrere Personen. |
| **Zone (H/V)** | ▬ | Eine **horizontale oder vertikale Zone** im Bild ist aktiv, der Rest wird ignoriert. | **Ideal: Zone auf den Kanzel-/Altar-Bereich legen.** |
| **Zone** | □ | Frei positionierbarer Zonen-Block. | Wenn der Predigtbereich unsymmetrisch liegt. |
| **1-Feld+** | ▢+ | Ein einzelnes Feld mit kleinem Sicherheitspuffer drumherum. | Eine einzelne, statische Person. |
| **1-Feld** | ▢ | Genau ein kleines Feld. | Sehr präzise auf einen festen Punkt. |
| **Punkt** | + | Punkt-Genauigkeit. | Selten praxistauglich für Video. |

**Was wir typischerweise nehmen:** **Zone (H/V)**, mit der Zone genau über den Kanzelbereich gelegt. Vorteil: Wenn jemand im Hintergrund vorbeiläuft, „kapert" das nicht den Fokus.

---

## 7.4 Drei Profile für typische Hosanna-Szenen

Statt sich durch alle Knöpfe zu wühlen, hier drei fertige Einstellungs-Pakete. Eines davon passt fast immer.

### Szene 1 — Statischer Prediger an der Kanzel (Standard-Profil)

Das ist das **Standard-Profil für 90 % der Hosanna-Streams**. Wenn man unsicher ist, mit diesem starten.

```
AF-Modus:                    Zone (Horizontal/Vertikal)
Zone-Position:               Auf Kanzel/Redner-Bereich zentriert
Fokusmodus:                  AFC (Continuous)
AF-Erkennungseinstellung:    ON
Motiverkennungs-Auswahl:     FACE/EYE
Dauer-AF:                    MODE 1
AF-Empfindlichkeit:          0
```

**Warum diese Kombination?**
- Die Zone schließt Bewegungen außerhalb des Kanzelbereichs aus → kein Hunting durch Hintergrundpersonen.
- AFC + Gesichts-/Augenerkennung sorgt dafür, dass die Augen scharf sind, sobald der Prediger leicht den Kopf bewegt.
- Empfindlichkeit 0 = ruhiger, träger AF — genau richtig für statische Szene.

### Szene 2 — Bewegter Chor / Anbetungsleitung

```
AF-Modus:                    AF-Gesamtbereich oder Verfolgung
Fokusmodus:                  AFC
AF-Erkennungseinstellung:    ON
Motiverkennungs-Auswahl:     FACE/EYE (oder HUMAN, falls Personen oft mit Rücken zur Kamera stehen)
Dauer-AF:                    MODE 1
AF-Empfindlichkeit:          +1 bis +2 (responsiver)
```

**Warum?** Bei mehreren bewegten Personen braucht der AF mehr Freiheit. AF-Gesamtbereich kann **bis zu 15 Gesichter gleichzeitig** erkennen (Körpererkennung bis 3 Personen). Per Joystick oder Touch-Display kann man zwischen den erkannten Gesichtern wechseln.

### Szene 3 — Weitwinkel-Gesamtansicht (mit Lumix 18-40)

```
AF-Modus:                    AF-Gesamtbereich
Fokusmodus:                  AFS oder AFC
AF-Erkennungseinstellung:    ON
Motiverkennungs-Auswahl:     HUMAN+ANIMAL
```

**Warum?** Bei Weitwinkel ist die **Schärfentiefe** ohnehin groß (= viel ist gleichzeitig scharf). AF muss hier nicht präzise arbeiten — Hauptsache, irgendetwas im Bild wird als scharf erkannt.

---

## 7.5 Motiverkennung — wen soll die Kamera erkennen?

**Menü-Pfad:** `Foto-/Videomenü → Fokus → AF-Erkennungseinstellung: ON` und dann `Motiverkennungs-Auswahl`.

| Option | Was wird erkannt? | Empfehlung |
|---|---|---|
| **FACE/EYE** | Gesichter frontal/halbprofil, Augen | **Standard für Hosanna** |
| **HUMAN** | Gesichter + Körper (auch von hinten) | Wenn Personen nicht immer frontal stehen |
| HUMAN+ANIMAL | Menschen + Tiere | Für die Kirche normalerweise nicht nötig |
| Tier / Auto / Motorrad / Flugzeug / Zug | spezifische Motive | Nicht für Kirche |

### So funktioniert die Anzeige im Live-Bild

- **Gelber Rahmen** = das Motiv, auf das die Kamera gerade fokussiert.
- **Weiße Rahmen** = weitere erkannte Motive (z. B. Gesichter im Hintergrund).
- Per **Joystick** oder **Touch** auf dem LCD kann man auf eine andere erkannte Person wechseln.

### Grenzen, die man kennen sollte

Die Gesichtserkennung versagt bei:
- stark abgeschatteten Gesichtern (Gegenlicht von vorne, Schatten auf dem Gesicht)
- Gesichtern fast außerhalb des Bildes (am Bildrand abgeschnitten)
- Profil-Ansichten über etwa 45° Drehung
- *Kein Problem:* dunkle Sonnenbrillen, Brillenträger.

---

## 7.6 Feineinstellungen — der AF wird trotzdem unruhig?

Es gibt zwei Stellschrauben, mit denen sich der AF-Charakter feinjustieren lässt.

**Menü-Pfad:** `Videomenü → Fokus → AF Custom Setting (Video)`

| Parameter | Was tut es? | Empfehlung |
|---|---|---|
| **AF-Empfindlichkeit** | Wie schnell reagiert der AF auf eine Veränderung? Negativ = träger, positiv = aggressiver. | **0** für statische Szene; **+1 bis +2** für bewegte. |
| **AF-Geschwindigkeit** | Wie schnell führt er den Fokus tatsächlich nach? | Mittel bis Schnell. |

**Faustregel:** Wenn der AF nervös pumpt, **Empfindlichkeit reduzieren** (auf -1, -2). Wenn er dem Prediger nicht folgt, **Empfindlichkeit erhöhen**.

### Dauer-AF

`Videomenü → Fokus → Dauer-AF`

| Modus | Verhalten |
|---|---|
| **MODE 1** | AF läuft nur **während** der Videoaufnahme. **Empfehlung — spart Energie.** |
| MODE 2 | AF läuft auch in Filmpausen. Mehr Stromverbrauch. |
| OFF | AF läuft im Video gar nicht. Nur für manuellen Fokus. |

### Quick-AF: ausschalten

`Individualmenü → Fokus/Auslöser → Quick-AF: OFF`

„Quick-AF" fokussiert ständig vor, auch ohne dass man auslöst. Verbraucht Strom und nutzt die Objektiv-Mechanik unnötig ab. Für Stativ-Streaming **immer aus**.

### Augen-Sensor-AF: ausschalten

`Individualmenü → Fokus/Auslöser → Augen-Sensor AF: OFF`

Ist nur relevant, wenn man durch den **Sucher** schaut. Wir nutzen den Monitor — also aus.

---

## 7.7 Probleme und Lösungen

### Problem: AF pumpt hin und her („Hunting")

Die häufigsten Ursachen:

- Zu wenig Kontrast im Motivbereich (z. B. einfarbige weiße Wand). Der AF findet keinen Schärfe-Anhaltspunkt.
- Bei langer Brennweite und sehr offener Blende: extrem schmale Schärfentiefe → der AF überschwingt leicht.
- AF-Empfindlichkeit zu hoch.
- Beim Samyang 35-150 bei f/2.8 am langen Ende in dunklen Szenen: bekanntermaßen anfällig (siehe [Kapitel 9](../lenses/samyang-35-150.md)).

**Lösungen, in der Reihenfolge ausprobieren:**
1. Blende auf f/3.5–4.0 schließen → mehr Schärfentiefe, AF wird stabiler.
2. AF-Empfindlichkeit auf 0 oder -1 reduzieren.
3. Statt AF-Gesamtbereich → Zone-AF auf den eigentlichen Motivbereich.
4. Als letzte Maßnahme: AF auf eine Fn-Taste legen und manuell auslösen („Back-Button-Focus") — die Kamera fokussiert dann nur, wenn ich die Taste drücke.

### Problem: Fokus festhalten für eine feste Position

Wenn der Prediger immer am gleichen Ort steht und der AF unnötig zappelt:

1. Per AFC auf das Gesicht fokussieren lassen.
2. Auf **AFS** umschalten **oder** AF per zugewiesener Taste pausieren.
3. Fokus bleibt fest, bis man wieder aktiviert.

---

## 7.8 Schnell-Referenz: empfohlene Standard-Einstellung

```
Fokusmodus:                  AFC (Continuous)
AF-Modus:                    Zone (H/V) auf Kanzel
AF-Erkennungseinstellung:    ON
Motiverkennungs-Auswahl:     FACE/EYE
Dauer-AF:                    MODE 1
Quick-AF:                    OFF
Augen-Sensor-AF:             OFF
AF-Empfindlichkeit:          0 (statisch) / +1 (Chor)
Joystick-Einstellung:        D.FOCUS (für schnelle AF-Feld-Verschiebung)
Bewegungsgesch. 1-Feld AF:   FAST
```
