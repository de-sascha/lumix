# Autofokus-Einstellungen — Panasonic Lumix DC-S5IIX für Kirchenstreaming

## Phase-Hybrid-Autofokus der S5IIX

Die S5IIX ist Panasonics erstes Modell mit **Phasen-Hybrid-AF**, das Phasenerkennung und Kontrastdetektion kombiniert:

- **779 Phasen-AF-Messpunkte** (100% Sensorabdeckung)
- **315 Kontrast-AF-Felder** (Feinabstimmung)
- Kombination: Phasen-AF für schnelle Vorfokussierung → Kontrast-AF für Feinschliff

## AF-Modi im Überblick

| AF-Modus | Symbol | Eignung für Kirche |
|---|---|---|
| **Verfolgung** | ₊₅ | Bewegte Motive (Chor, Prediger der sich bewegt) |
| **AF-Gesamtbereich** | ▦ | Spontane Situationen, mehrere Personen |
| **Zone (H/V)** | ▬ | **Ideal: Zone auf Kanzel/Altar legen** |
| **Zone** | □ | Flexible Zone, frei positionierbar |
| **1-Feld+** | ▢+ | Einzelne Person mit Sicherheitspuffer |
| **1-Feld** | ▢ | Präzise auf einen Bereich |
| **Punkt** | + | Höchste Präzision, wenig praxistauglich für Video |

## Empfohlene Konfiguration: Kirchengottesdienst

### Szenario 1: Statischer Prediger an der Kanzel

```
AF-Modus:                Zone (Horizontal/Vertikal)
Zone-Position:           Auf Kanzel/Redner-Bereich zentriert
Fokusmodus:              AFC (Continuous)
AF-Erkennungseinstellung: ON
Motiverkennungs-Auswahl: FACE/EYE
Dauer-AF:                MODE 1
```

**Begründung:** Die horizontale/vertikale Zone begrenzt den AF-Bereich auf den Kanzelbereich. Selbst wenn sich jemand im Hintergrund bewegt, bleibt der Fokus auf dem Redner. Gesichts-/Augenerkennung verfeinert den Fokus innerhalb der Zone.

### Szenario 2: Bewegter Chor / Anbetungsleitung

```
AF-Modus:                AF-Gesamtbereich oder Verfolgung
Fokusmodus:              AFC (Continuous)
AF-Erkennungseinstellung: ON
Motiverkennungs-Auswahl: FACE/EYE (oder HUMAN)
Dauer-AF:                MODE 1
AF-Empfindlichkeit:      +1 bis +2 (responsiver)
```

**Begründung:** Bei mehreren sich bewegenden Personen braucht der AF mehr Freiheit. AF-Gesamtbereich erkennt bis zu 15 Gesichter gleichzeitig (Körpererkennung bis 3 Personen). Per Joystick oder Touch kann zwischen erkannten Gesichtern gewechselt werden.

### Szenario 3: Weitwinkel-Gesamtansicht (18-40mm)

```
AF-Modus:                AF-Gesamtbereich
Fokusmodus:              AFS oder AFC
AF-Erkennungseinstellung: ON
Motiverkennungs-Auswahl: HUMAN+ANIMAL
```

**Begründung:** Bei Weitwinkel ist die Schärfentiefe ohnehin groß. AF-Gesamtbereich reicht aus.

## AF-Erkennungseinstellungen

**Fotomenü/Videomenü > Fokus > AF-Erkennungseinstellung: ON**

### Motiverkennungs-Auswahl

| Option | Erkennt | Empfehlung |
|---|---|---|
| **FACE/EYE** | Gesichter frontal, Augen | **Standard für Kirchenstreaming** |
| **HUMAN** | Gesichter + Körper (auch von hinten) | Gut wenn Personen nicht immer frontal zur Kamera |
| **HUMAN+ANIMAL** | Menschen + Tiere | Nicht nötig für Kirche |

### Empfehlung: **FACE/EYE** für den Haupteinsatz

- Erkennt Gesichter frontal und im Halbprofil
- Augenerkennung fokussiert präzise auf die Augen
- Bis zu 15 Gesichter gleichzeitig erkennbar
- Bei mehreren Personen: gelber Rahmen = aktiver Fokus, weiße Rahmen = erkannt
- Per Joystick oder Touch auf andere Person wechseln

### Grenzen der Gesichtserkennung

- Stark abgeschattete Gesichter
- Personen am Bildrand (fast abgeschnitten)
- Gesichter von der Seite (>45°)
- Große dunkle Sonnenbrillen → kein Problem für S5IIX
- Brillenglas → wird korrekt erkannt

## AF-Feineinstellungen für Video

### AF Custom Setting (Video)

**Videomenü > Fokus > AF Custom Setting (Video)**

| Parameter | Empfehlung | Erklärung |
|---|---|---|
| AF-Empfindlichkeit | 0 (statisch) / +1 (bewegte Szene) | Wie schnell AF auf Änderungen reagiert |
| AF-Geschwindigkeit | Mittel bis Schnell | Wie schnell der Fokus überfährt |

- **Statischer Prediger:** Empfindlichkeit auf 0 (verhindert Hunting wenn jemand vor der Kamera vorbeiläuft)
- **Bewegte Szene:** Empfindlichkeit auf +1 bis +2

### Dauer-AF

**Videomenü > Fokus > Dauer-AF: MODE 1**

- MODE 1: AF nur während Videoaufnahme aktiv → spart Strom
- MODE 2: AF auch in Filmpausen aktiv → höherer Energieverbrauch

### Quick-AF

**Individualmenü > Fokus/Auslöser > Quick-AF: OFF**

Der Quick-AF (ständige Vorfokussierung ohne Auslöser-Betätigung) verbraucht viel Strom und belastet Objektiv-Mechanik. Für Streaming auf Stativ nicht nötig → **ausschalten**.

### Augen-Sensor AF

**Individualmenü > Fokus/Auslöser > Augen-Sensor AF: OFF (für Stativ-Betrieb)**

Nur relevant wenn man durch den Sucher blickt. Bei Stativ-Betrieb mit Monitor irrelevant.

## Fokus-Probleme und Lösungen

### AF-Hunting (Fokus "pumpt" hin und her)

**Ursachen:**
- Zu wenig Kontrast im Motivbereich (einfarbige Wand)
- Zu offene Blende bei langer Brennweite
- AF-Empfindlichkeit zu hoch eingestellt
- Samyang 35-150mm bei f/2.8 am langen Ende in Low-Light

**Lösungen:**
- Blende auf f/3.5-4.0 schließen (mehr Schärfentiefe)
- AF-Empfindlichkeit auf 0 oder -1 reduzieren
- Zone-AF statt AF-Gesamtbereich verwenden
- Alternativ: AF auf Fn-Taste legen und manuell auslösen (Back-Button-Focus)

### Fokus-Lock für feste Position

Wenn der Prediger immer am gleichen Ort steht:
1. AFC mit Gesichtserkennung fokussieren lassen
2. Auf AFS wechseln oder AF per Touch-Button (AF OFF) pausieren
3. Fokus bleibt fix bis zur nächsten AF-Aktivierung

## Bewegungsgeschwindigkeit 1-Feld AF

**Foto/Videomenü > Fokus > Bewegungsgesch. 1-Feld AF**

| Einstellung | Wirkung |
|---|---|
| **FAST** | AF-Feld bewegt sich schneller über das Bild |
| NORMAL | Standard-Geschwindigkeit |

Empfehlung: **FAST** — schnelleres Umpositionieren per Joystick falls nötig.

## Zusammenfassung: Empfohlene AF-Einstellung

```
Fokusmodus:              AFC (Continuous)
AF-Modus:                Zone (H/V) auf Kanzel
AF-Erkennungseinstellung: ON
Motiverkennungs-Auswahl: FACE/EYE
Dauer-AF:                MODE 1
Quick-AF:                OFF
AF-Empfindlichkeit:      0 (statisch) / +1 (Chor)
Joystick-Einstellung:    D.FOCUS (für schnelle AF-Feld-Verschiebung)
Bewegungsgesch. 1-Feld:  FAST
```
