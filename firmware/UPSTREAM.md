# Proveniența firmware-ului

- Sursă: <https://github.com/hiveeyes/hanimandl>
- Commit: `f425e1e127b3c9cf5b944ea19559c622f7923754` (2026-09-15), HaniMandl **v0.2.13**
  cu suport Heltec WiFi Kit 32 V3 / ESP32-S3 (Arduino Core 3.x, pioarduino)
- Fișier: `hanimandl.cpp` → copiat ca `src/hanimandl.cpp`
- Licență: GPLv3 (vezi `../LICENSE`)

## Modificări față de upstream

Una singură – activarea inversării servo-ului, cerută de autorul modelului Printables
pentru angrenajul cu roți dințate:

```diff
-//#define QUETSCHHAHN_LINKS       // Servo invertieren, falls der Quetschhahn von links geöffnet wird. Mindestens ein Exemplar bekannt
+#define QUETSCHHAHN_LINKS       // Servo invertieren, falls der Quetschhahn von links geöffnet wird. Mindestens ein Exemplar bekannt
+                                // [nalex09] ACTIVAT: necesar pentru angrenajul cu roti dintate al modelului Printables 524971 (rallef80)
```

`platformio.ini` este cel din upstream, cu mediul redenumit `heltec_v3`, bibliotecile scrise cu
numele complet din registry (`bogde/HX711`, `olikraus/U8g2`, `madhephaestus/ESP32Servo`) și
`upload_speed` adăugat.

## Binarul din `bin/`

`bin/hanimandl-v0.2.13-heltec-v3-factory.bin` este `firmware.factory.bin` generat de `pio run`
din aceste surse (bootloader + tabel partiții + aplicație, se scrie la adresa **0x0**), compilat cu
framework-arduinoespressif32 3.3.12, HX711 0.7.5, U8g2 2.37.1, ESP32Servo 3.2.1.

SHA-256: `450ba755ca8896675ab96c9765bbfac76dfaf5ce530cecab5696d7811363a771`

Dacă modifici `src/hanimandl.cpp`, binarul nu se actualizează singur: recompilează (`pio run`) sau
descarcă artefactul generat de GitHub Actions (tab-ul *Actions* → ultimul build → *Artifacts*).

## Actualizare la o versiune upstream nouă

```bash
curl -L -o src/hanimandl.cpp https://raw.githubusercontent.com/hiveeyes/hanimandl/main/hanimandl.cpp
# apoi reactivează linia:  #define QUETSCHHAHN_LINKS
```
