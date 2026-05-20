# Firmware-Dateien

Hier liegen die heruntergeladenen Firmware-Binaries. **Nicht in Git eingecheckt** (siehe `.gitignore`).

## Aktuell

| Datei | Version | Datum | Größe | Quelle |
|---|---|---|---|---|
| `S5m2XV27.zip` | 2.7 | 10.03.2026 | 157.760.717 Bytes | https://av.jpn.support.panasonic.com/support/global/cs/dsc/download/ff/dl/s5m2x.html |

SHA-256 (S5m2XV27.zip):
`363b2cda212706e9f6c63cabbfcdace41fb3428283dfa9f657854bedba284b50`

## Update-Prozess

1. ZIP entpacken → `S5m2XV27.bin`
2. Datei ins Root-Verzeichnis einer FAT/exFAT-formatierten SD-Karte kopieren
3. SD-Karte in **Slot 1** der S5IIX einlegen
4. Akku **>50%** sicherstellen (oder Netzteil)
5. Kamera einschalten
6. Setup-Menü > Sonstige > Firmware-Anz. > Update ausführen
7. ⚠ Nicht ausschalten während des Updates
8. Nach dem Update: LUMIX Flow / Lab / Sync / Tether ebenfalls aktualisieren
