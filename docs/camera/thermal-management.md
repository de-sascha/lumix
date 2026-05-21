# Kapitel 5 — Thermomanagement und Lüfter

> Teil II, Kapitel 5 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [4. Stromversorgung und Standby](power-management.md). Nächstes Kapitel: [6. Videoeinstellungen](video-settings.md).

## Worum geht es hier?

Kameras werden bei langen Videoaufnahmen warm. Bei vielen spiegellosen Kameras führt das nach 20–40 Minuten zu einer Notabschaltung — sehr schlechte Eigenschaft für Live-Streaming.

Die S5IIX hat als eine der wenigen spiegellosen Kameras einen **eingebauten aktiven Lüfter** (sitzt unter dem Suchergehäuse). Damit kann sie theoretisch *unbegrenzt* aufnehmen. „Theoretisch" deshalb, weil zwei Einstellungen passen müssen: **Lüfter-Modus** und **Temperaturmanagement**. Dieses Kapitel erklärt beide und gibt die für unseren Streaming-Einsatz richtige Kombination.

> **Bisher in der Praxis bestätigt:** 2× 3,5 Stunden 4K-Daueraufnahme ohne Probleme (Hitzetest am 2026-05-21). Streaming-Einsatz selbst ist auch unkritisch.

---

## 5.1 Lüfter-Modus

**Menü-Pfad:** `Setup-Menü → EIN/AUS → Lüfter Modus`

Der Lüfter-Modus regelt, **wann** und **wie schnell** der Lüfter läuft. Sechs Modi stehen zur Auswahl:

| Modus | Verhalten | Für uns geeignet? |
|---|---|---|
| **AUTO1** | Lüfter startet früh und proaktiv, Kühlung hat Vorrang. | Nur bei extremen Formaten (z. B. 4K 60p ALL-Intra). |
| **AUTO2** | Lüfter startet erst, wenn die Temperatur tatsächlich steigt. | **Empfehlung für Hosanna** — guter Kompromiss. |
| **FAST** | Lüfter läuft permanent auf hoher Drehzahl. | Hörbar; nur sinnvoll, wenn das Mikrofon weit weg ist. |
| **NORMAL** | Lüfter läuft permanent auf mittlerer Drehzahl. | Leises Rauschen. |
| **SLOW** | Lüfter läuft permanent auf niedriger Drehzahl. | Praktisch unhörbar, aber begrenzte Kühlleistung. |
| **OFF** | Lüfter aus. | **Nicht für Video!** Nur Foto. |

### Empfehlung für Hosanna: AUTO2

Begründung:
- Der Gemeindesaal ist klimatisiert, typisch 18–25 °C. In diesem Bereich wird die S5IIX gar nicht so warm, dass der Lüfter überhaupt anspringen muss.
- Mit AUTO2 ist die Kamera die meiste Zeit lautlos — der Lüfter startet nur, wenn er gebraucht wird.
- Sollte er doch starten: Wir nutzen das **Kamera-Audio gar nicht** (das Mikrofon hängt am Audio-Interface, nicht an der Kamera). Lüftergeräusch landet also nie auf der Aufnahme.

Praktisch heißt das: AUTO2 reicht für unser Setup. FAST/NORMAL wären nur nötig, wenn man die Kamera in heißer Umgebung über viele Stunden quälen würde.

---

## 5.2 Temperaturmanagement

**Menü-Pfad:** `Setup-Menü → Monitor/Display 1 → Temperaturmanagement`

Diese Einstellung legt fest, **wie heiß die Kamera werden darf, bevor sie sich abschaltet**.

| Option | Verhalten |
|---|---|
| **STANDARD** | Sobald die interne Temperatur eine konservative Schwelle erreicht, **stoppt die Aufnahme sofort**. |
| **HIGH** | Die Kamera darf deutlich wärmer werden. Aufnahme läuft weiter, ggf. mit Warnsymbol. |

### Empfehlung für Hosanna: HIGH

Begründung:
- Auf STANDARD könnte die Kamera nach 1–2 Stunden Streaming ohne erkennbaren Grund anhalten — fatal mitten im Gottesdienst.
- HIGH verlängert die zulässige Aufnahmezeit erheblich.
- Die Kamera sitzt auf dem Stativ, niemand fasst sie an. Dass sie warm wird, stört in dieser Konfiguration niemanden.

> **Achtung:** HIGH heißt nicht „beliebig heiß". Bei kritischer Temperatur erscheint ein Warnsymbol auf dem Display. Wenn das auftaucht: Aufnahme nach Möglichkeit beenden, Kamera abkühlen lassen.

---

## 5.3 Wärme-Reduktion: was hilft sonst noch?

Wenn man trotz AUTO2 + HIGH die Kamera weiter entlasten möchte, helfen folgende Maßnahmen — sortiert nach Wirkung:

| Maßnahme | Wirkung |
|---|---|
| **Nur HDMI-Ausgabe, keine interne Aufnahme** | Größte Einzelmaßnahme. Encoder muss dann fast nichts tun. *(Aber: wir nutzen interne FHD-Backup-Aufnahme als Ruhemodus-Schutz, siehe [Kapitel 4.3](power-management.md#43-doppel-sicherung-internes-backup-recording).)* |
| **1080p statt 4K über HDMI ausgeben** | Weniger Prozessorlast. |
| **25p statt 50p** | Halbe Prozessorlast. |
| **IBIS ausschalten** | Auf dem Stativ ohnehin nicht nötig; spart etwas Sensor-Wärme. „IBIS" = In-Body Image Stabilizer, der Sensor-Bildstabilisator. |
| **LCD aufgeklappt lassen** | Wirkt als zusätzliche Kühlfläche. Für unseren *Stresstest* klappen wir es bewusst ein, um die Kamera zu fordern; im Live-Einsatz lieber aufklappen. |
| **Cage/Gehäuse, das die Lüftung blockiert, vermeiden** | Luftzirkulation muss frei sein. |
| **Keine direkte Sonneneinstrahlung** | Bei Outdoor-Events offensichtlich, in der Kirche selten ein Thema. |

---

## 5.4 Warnsignale erkennen

Auf dem Display der Kamera kann ein **Thermometer-Symbol** erscheinen. Bedeutung:

- **Symbol erscheint:** Kamera nähert sich der Temperaturgrenze.
- Bei **Temperaturmanagement = STANDARD**: kurz darauf Aufnahme-Stopp.
- Bei **Temperaturmanagement = HIGH**: Kamera arbeitet weiter, hält die Warnung nur sichtbar.

Wenn das Symbol im Live-Einsatz auftaucht: ruhig bleiben, weiterlaufen lassen. Nach dem Stream: Lüfter-Modus überdenken, ggf. von AUTO2 auf NORMAL umstellen, oder Raumtemperatur prüfen.

---

## 5.5 Praxistest empfohlen — bevor es live geht

Vor dem ersten echten Live-Einsatz mit einer neuen Konfiguration:

- Kamera in der finalen Konfiguration aufbauen (HDMI-Output, Lüfter AUTO2, Temperaturmgmt HIGH)
- **Mindestens 60 Minuten** durchlaufen lassen, idealer 2–3 Stunden
- Beobachten: erscheint ein Thermometer-Symbol? Hält sie wirklich durch?

Ergebnis vom 2026-05-21: 2× 3,5 Stunden 4K-Daueraufnahme **bestanden**. Streaming-Last allein ist deutlich geringer als reine 4K-Aufnahme; sollte also problemlos laufen.

---

## 5.6 Zusammenfassung Hosanna-Setup

```
Lüfter Modus:           AUTO2
Temperaturmanagement:   HIGH
Interne Aufnahme:       FHD 25p H.264 (Backup, siehe Kapitel 4.3)
IBIS:                   AUS (Stativ)
LCD:                    Aufgeklappt
HDMI-Output:            4K25 oder 1080p25
```
