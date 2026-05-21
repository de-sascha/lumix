# Stromversorgung & Standby-Vermeidung — Panasonic Lumix DC-S5IIX

## USB Power Delivery (USB-PD)

Die S5IIX unterstützt USB-PD über den USB-C-Anschluss. Das ermöglicht Dauerbetrieb bei gleichzeitigem Laden des eingelegten Akkus.

### Technische Anforderungen

| Parameter | Wert |
|---|---|
| USB-PD Profil | 9V / 3A (27W) Minimum |
| Anschluss | USB-C (am Kameragehäuse) |
| Verhalten | Kamera läuft über USB-PD, Akku wird gleichzeitig geladen |
| Failover | Bei USB-Trennung nahtloser Wechsel auf Akku |

### Empfohlene Netzteile

- Mindestens 30W USB-PD Netzteil mit 9V/3A Profil
- Kurzse, hochwertige USB-C Kabel (zertifiziert für PD)
- Beispiele: Anker Nano 30W, Apple 30W USB-C, RAVPower 30W PD

### Wichtige Hinweise aus dem Handbuch

- Akku muss eingelegt sein (Kamera funktioniert NICHT ohne Akku über USB-PD)
- Laden dauert bei eingeschalteter Kamera länger als bei ausgeschalteter
- Nicht über USB-Hubs oder Tastatur-USB-Ports anschließen
- Bei USB-PD-inkompatiblen Geräten: nur Stromversorgung, kein Laden
- Akkustand kann trotz USB-PD unter bestimmten Bedingungen sinken (hohe Last)

## Standby/Sleep-Vermeidung

### ⚠️ Bekannter Vorfall (Mai 2026)

Während eines Gottesdienst-Streams ist die S5IIX unerwartet ausgegangen. Diagnose ergab: **Ruhemodus war auf 5 Min aktiv**. Die Kamera hat HDMI-Out alleine NICHT als Aktivität erkannt und nach 5 Min Inaktivität abgeschaltet — entgegen der Handbuch-Aussage, dass HDMI-Out den Standby verhindern soll.

**Konsequenz:** ALLE Standby-Trigger explizit auf AUS setzen, dem Handbuch nicht blind vertrauen.

### Kritische Einstellungen (verifiziert FW 2.6, deutsches Menü)

Menü-Pfad: **MENU → 🔧 Setup → EIN/AUS → Sparmodus**

| Einstellung | Standard (Werk) | Empfehlung Streaming | Begründung |
|---|---|---|---|
| **Ruhemodus** | 5 Min | **AUS** | Hauptursache des Mai-2026-Vorfalls. Schaltet Kamera komplett ab. |
| **Ruhemodus (Wi-Fi)** | EIN | **AUS** | Greift zusätzlich auch mit Wi-Fi-Verbindung. |
| **Sucher (LVF)** | 5 Min | **AUS** | Wir nutzen LCD/HDMI, nicht den Sucher — sicherheitshalber AUS. |
| **Energiespar-Sucheraufn. → Zeit bis zur Ruhe** | — | **OFF** | Verhindert Standby bei eingeklapptem LCD. |
| **Ruhe-Modus Aktivierung** | Control Panel | Control Panel | Reine Anzeige-Option, mit Ruhemodus=AUS irrelevant. |

### Power Save Mode ist AUTOMATISCH DEAKTIVIERT bei (laut Handbuch):

- Während Videoaufnahme/Videowiedergabe
- Bei PC-Verbindung
- Bei Time Lapse Shot
- Bei Stop Motion Animation (Auto Shooting)
- Bei Live View Composite
- Bei Focus Transition
- Während Slide Show
- **Während HDMI-Output für Aufnahme** ← in der Praxis NICHT zuverlässig (s. Vorfall oben!)

**Wichtig:** Trotz Handbuch-Aussage hat HDMI-Output die Kamera in der Praxis NICHT zuverlässig wach gehalten. Standby-Modi explizit ausschalten ist Pflicht, nicht optional.

### Doppel-Sicherung: Internes Backup-Recording

Zusätzlich zur HDMI-Ausgabe ein **internes FHD-Recording auf SD-Karte** mitlaufen lassen:

- Kamera ist „beschäftigt" — Standby-Trigger greifen unter keinen Umständen
- Backup-Video falls der Stream-PC abstürzt
- Bei FHD 25p H.264 thermisch unkritisch (3-5h+ stabil)

## Empfohlenes Power-Setup für Kirchenstreaming

### Primär: USB-PD + Akku als USV

```
┌─────────────────┐     USB-C     ┌─────────────┐
│ 30W USB-PD      │───────────────│ S5IIX       │
│ Netzteil        │               │ (Akku BLK22 │
│ (an Steckdose)  │               │  eingelegt)  │
└─────────────────┘               └─────────────┘
```

**Vorteile:**
- Unbegrenzte Laufzeit
- Akku als automatische USV (jemand stolpert über Kabel → kein Ausfall)
- Ein voller BLK22 gibt ca. 70-90 Min. Video-Backup

### Alternative: DC-Koppler DMW-DCC17 (Dummy-Akku)

```
┌─────────────────┐     DC        ┌─────────────┐
│ AC-Adapter +    │───────────────│ S5IIX       │
│ DC-Koppler      │               │ (kein Akku) │
│ DMW-DCC17       │               │             │
└─────────────────┘               └─────────────┘
```

**Vorteile:**
- Garantiert unbegrenzte Laufzeit
- Kein Akku-Wärme-Problem

**Nachteile:**
- KEIN Failover bei Stromausfall → Kamera schaltet sofort ab!
- Batteriefach schließt nicht komplett (kosmetisch)

### Dritte Option: Battery Grip DMW-BGS5

- Nimmt zweiten BLK22-Akku auf
- Kein USB-PD-Passthrough (USB muss an Kameragehäuse)
- 2x BLK22 ≈ 2,5-3 Stunden HDMI-Output
- Nur sinnvoll wenn USB-PD nicht möglich ist

## Empfehlung

**USB-PD mit eingestecktem vollgeladenem Akku** — die zuverlässigste Lösung:
- Dauerbetrieb garantiert
- Automatisches Failover bei Stromunterbrechung
- Prüfen ob Akku auf >50% bleibt während des Betriebs (sonst stärkeres Netzteil verwenden)

## Checkliste vor dem Gottesdienst

- [ ] USB-PD Netzteil angeschlossen und Kamera zeigt Lade-Symbol
- [ ] Akku BLK22 voll geladen eingelegt
- [ ] **Ruhemodus: AUS** (nicht 5 Min!)
- [ ] **Ruhemodus (Wi-Fi): AUS**
- [ ] **Sucher (LVF): AUS**
- [ ] Energiespar-Sucheraufn. → Zeit bis zur Ruhe: OFF
- [ ] Lüfter Modus: AUTO2
- [ ] Temperaturmanagement: HIGH (Setup → Monitor → Temperaturmgmt)
- [ ] Internes FHD-Backup-Recording aktiv (Doppel-Sicherung)
- [ ] HDMI-Kabel fest angeschlossen
- [ ] **15-Min-Test:** Kamera aufbauen, nicht anfassen, prüfen ob sie an bleibt
