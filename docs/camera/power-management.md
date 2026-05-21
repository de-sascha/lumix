# Kapitel 4 — Stromversorgung und Standby

> Teil II, Kapitel 4 des [S5IIX-Handbuchs](../../README.md). Voriges Kapitel: [3. Firmware-Stand](firmware-changelog.md). Nächstes Kapitel: [5. Thermomanagement und Lüfter](thermal-management.md).

## Worum geht es hier?

Damit die Kamera einen ganzen Gottesdienst durchhält, müssen zwei Dinge stimmen:

1. **Sie bekommt zuverlässig Strom** — nicht nur 70 Minuten aus einem Akku.
2. **Sie schaltet sich nicht selbst ab.** Die S5IIX hat im Werks-Zustand eingebaute Spar-Modi, die die Kamera nach 5 Minuten Inaktivität ausschalten. Genau das ist uns im Mai 2026 mitten im Stream passiert ([Kapitel 16](standby-incident-2026-05.md)).

Wer dieses Kapitel beachtet, hat damit zwei der größten Risiken eines Live-Einsatzes (leere Batterie, Auto-Off) erledigt.

---

## 4.1 Stromversorgung: drei Wege

Die S5IIX kann auf drei Arten mit Strom versorgt werden. Wir nutzen **Variante A**.

### Variante A — USB Power Delivery (empfohlen)

Die Kamera hängt an einem USB-C-Netzteil und betrieben wird, gleichzeitig liegt im Akkufach ein voller Akku. Fällt das Netzteil aus (jemand stolpert über das Kabel), übernimmt der Akku **nahtlos** — wie eine kleine USV (unterbrechungsfreie Stromversorgung).

```
┌─────────────────┐     USB-C     ┌──────────────┐
│ 30W USB-PD      │───────────────│ S5IIX        │
│ Netzteil        │               │ (Akku BLK22  │
│ (Steckdose)     │               │  eingelegt)  │
└─────────────────┘               └──────────────┘
```

**Was ist „USB-PD"?** USB Power Delivery — ein Standard, mit dem ein USB-C-Netzteil mehr als die üblichen 5 V liefern kann. Die Kamera braucht **9 V bei 3 A** (= 27 W). Normale Handy-Ladegeräte können das oft nicht; man braucht ein PD-fähiges Netzteil.

| Anforderung | Wert |
|---|---|
| USB-PD Profil | mindestens 9 V / 3 A (27 W) |
| Empfohlene Netzteil-Leistung | 30 W oder mehr |
| Anschluss | USB-C am Kameragehäuse |
| Kabel | USB-C-Kabel mit PD-Zertifizierung, möglichst kurz (≤ 1,5 m) |

**Was passiert während des Betriebs?** Die Kamera läuft direkt aus dem Netzteil. Der eingelegte Akku wird parallel geladen — bei eingeschalteter Kamera langsamer als bei ausgeschalteter. Das ist normal.

**Was muss man wissen?**
- **Akku muss eingelegt sein.** Die S5IIX läuft bei USB-PD nicht ohne Akku im Fach. (Anders als manche andere Kameras.)
- **Nicht über USB-Hubs oder Tastatur-Ports.** Die liefern oft nicht stabil 9 V/3 A.
- Bei sehr hoher Last (4K-Aufnahme, voll aufgedrehtem Lüfter) kann der Akku trotz Netzteil leicht entladen. Wenn das passiert, ist das Netzteil zu schwach.

**Bewährte Netzteile:** Anker Nano 30 W, Apple 30 W USB-C, RAVPower 30 W PD.

### Variante B — DC-Koppler (Dummy-Akku)

Ein „DC-Koppler" ist ein Bauteil in Akku-Form, das in das Akkufach gesteckt wird und über ein Kabel direkt mit einem AC-Adapter verbunden ist. Panasonic-Bezeichnung: **DMW-DCC17**.

```
┌─────────────────┐     DC        ┌──────────────┐
│ AC-Adapter +    │───────────────│ S5IIX        │
│ DC-Koppler      │               │ (kein Akku!) │
│ DMW-DCC17       │               │              │
└─────────────────┘               └──────────────┘
```

**Vorteil:** Garantierte unbegrenzte Laufzeit, kein Akku der warm wird.

**Nachteil:** **Kein Failover.** Bei Stromausfall geht die Kamera sofort aus — es gibt keinen Akku, der einspringt. Für Live-Streaming **nicht empfohlen**, deshalb nutzen wir Variante A.

### Variante C — Battery Grip DMW-BGS5

Ein Zusatzgriff, der einen zweiten BLK22-Akku aufnimmt. Verdoppelt die Akku-Laufzeit auf etwa 2,5–3 Stunden HDMI-Output.

**Nachteil:** Es gibt kein USB-PD-Passthrough — wenn man USB-PD nutzen will, muss das USB-Kabel direkt am Kameragehäuse stecken, nicht am Griff. Für unser Setup also kaum sinnvoll.

---

## 4.2 Standby/Sleep deaktivieren

### Warum das wichtig ist

Die S5IIX hat **mehrere unabhängige Spar-Mechanismen**, die jeweils eigenständig die Kamera ausschalten können. Im Werks-Zustand sind sie alle aktiv. Ergebnis: Die Kamera schaltet sich nach wenigen Minuten Stille selbst aus — auch wenn sie ein HDMI-Signal sendet.

Das offizielle Handbuch behauptet, HDMI-Output deaktiviere die Sparmodi automatisch. **In der Praxis stimmt das nicht zuverlässig.** Bei uns hat genau dieses Verhalten im Mai 2026 zum Stream-Abbruch geführt (siehe [Kapitel 16](standby-incident-2026-05.md)).

**Konsequenz:** Wir verlassen uns nicht aufs Handbuch — wir schalten **alle** Spar-Trigger explizit aus.

### Die Einstellungen

**Menü-Pfad:** `MENU → 🔧 Setup → EIN/AUS → Sparmodus`

| Einstellung | Werks-Default | Unser Wert | Warum |
|---|---|---|---|
| **Ruhemodus** | 5 Min | **AUS** | Hauptursache des Mai-2026-Vorfalls — schaltet die Kamera komplett ab. |
| **Ruhemodus (Wi-Fi)** | EIN | **AUS** | Zweiter unabhängiger Trigger; greift auch, wenn Wi-Fi an ist. |
| **Sucher (LVF)** | 5 Min | **AUS** | „LVF" = Live View Finder, der elektronische Sucher. Wir nutzen ihn nicht — sicherheitshalber AUS. |
| **Energiespar-Sucheraufn. → Zeit bis zur Ruhe** | — | **OFF** | Greift, wenn das LCD eingeklappt ist. |
| **Ruhe-Modus Aktivierung** | Control Panel | Control Panel | Reine Anzeige-Option; mit Ruhemodus=AUS ohnehin egal. |

> **Wichtig:** Diese Schalter sind unabhängig. Es reicht **nicht**, einen davon auszuschalten — alle drei (Ruhemodus, Ruhemodus Wi-Fi, Sucher LVF) müssen einzeln auf AUS.

### Was das Handbuch zur HDMI-Frage sagt — und warum wir trotzdem alles ausschalten

Laut Panasonic-Handbuch wird der Sparmodus „automatisch deaktiviert" während:

- Videoaufnahme/Videowiedergabe
- PC-Verbindung
- Time-Lapse, Stop-Motion, Live View Composite, Focus Transition, Slide Show
- **HDMI-Output für Aufnahme** ← in der Praxis nicht zuverlässig

Das letzte ist genau unser Anwendungsfall, und genau dort hat es bei uns versagt. Wir gehen davon aus, dass eine externe Capture-Karte (Blackmagic DeckLink) der Kamera nicht das Signal gibt, das sie als „aktive HDMI-Aufnahme" interpretiert. Konsequenz wie oben: Spar-Modi explizit aus.

---

## 4.3 Doppel-Sicherung: internes Backup-Recording

Zusätzlich zur HDMI-Ausgabe lassen wir parallel eine **interne Aufnahme** auf SD-Karte mitlaufen. Das hat zwei Vorteile gleichzeitig:

1. **Die Kamera ist „aktiv beschäftigt".** Während eine Videoaufnahme läuft, greifen die Standby-Trigger garantiert nicht — auch in unserem ungünstigen HDMI-Capture-Szenario.
2. **Wir haben ein Backup-Video.** Wenn der Streaming-PC abstürzt oder das Internet ausfällt, ist der Gottesdienst trotzdem aufgezeichnet.

Empfohlene Backup-Einstellung: **FHD 25p H.264 LongGOP (≈ 100 Mbps)**. Thermisch unkritisch, läuft auch über mehrere Stunden stabil. Details zu den Format-Codes in [Kapitel 6](video-settings.md).

---

## 4.4 Checkliste vor dem Gottesdienst

Strikt von oben nach unten abarbeiten — die letzten Punkte sind genauso wichtig wie die ersten.

- [ ] USB-PD-Netzteil eingesteckt, Kamera zeigt das Lade-Symbol
- [ ] Akku BLK22 voll geladen im Akkufach
- [ ] Ruhemodus: **AUS** (nicht 5 Min!)
- [ ] Ruhemodus (Wi-Fi): **AUS**
- [ ] Sucher (LVF): **AUS**
- [ ] Energiespar-Sucheraufn. → Zeit bis zur Ruhe: **OFF**
- [ ] Lüfter Modus: AUTO2 *(siehe [Kapitel 5](thermal-management.md))*
- [ ] Temperaturmanagement: HIGH *(siehe [Kapitel 5](thermal-management.md))*
- [ ] Internes FHD-Backup-Recording aktiv (Doppel-Sicherung)
- [ ] HDMI-Kabel fest angeschlossen, Kabelhalter gesichert
- [ ] **15-Minuten-Test:** Kamera aufbauen, **nicht anfassen**, prüfen ob sie an bleibt

→ Wenn der 15-Minuten-Test versagt: zurück zu 4.2 und alle drei Schalter prüfen. Erst weitermachen, wenn die Kamera sicher wach bleibt.
