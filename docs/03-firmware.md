# 3. Firmware – compilare și încărcare pe Heltec V3

Codul din [`firmware/src/hanimandl.cpp`](../firmware/src/hanimandl.cpp) este HaniMandl **v0.2.13**
(upstream [hiveeyes/hanimandl](https://github.com/hiveeyes/hanimandl)), cu o singură modificare:

```cpp
#define QUETSCHHAHN_LINKS   // activat
```

Autorul modelului Printables cere explicit această linie: fără ea, angrenajul cu roți dințate inversează
sensul de rotație, iar servo-ul ar **deschide** robinetul când firmware-ul vrea să-l închidă.
Detalii în [`firmware/UPSTREAM.md`](../firmware/UPSTREAM.md).

> ⚠️ **Nu folosi binarul oficial `hani-mandl_v0.2.13_heltec-v3-combined.bin`** de pe GitHub-ul upstream
> pentru acest model: e compilat **fără** `QUETSCHHAHN_LINKS`.

Înainte de orice: conectează placa la PC cu un cablu USB-C **de date** (nu doar de încărcare).
Pe Windows poate fi nevoie de driverul **Silicon Labs CP210x** pentru portul serial al plăcii.

---

## Varianta rapidă: binar gata compilat, din browser (fără instalări)

În [`firmware/bin/`](../firmware/bin/) există `hanimandl-v0.2.13-heltec-v3-factory.bin`, compilat din
sursele acestui repo (cu `QUETSCHHAHN_LINKS` activ).

1. Descarcă fișierul `.bin` (pe GitHub: deschide fișierul → butonul *Download raw file*).
2. Deschide în **Chrome** sau **Edge**: <https://espressif.github.io/esptool-js/>
3. *Connect* → alege portul plăcii (dacă nu apare, vezi „Dacă încărcarea nu pornește” mai jos).
4. La **Flash Address** scrie `0x0`, alege fișierul `.bin`, apasă **Program**.
5. După „Leaving…”, apasă **RST** pe placă.

Binarul folosește setările implicite (encoder KY-040, `ROTARY_SCALE 2`). Dacă ai nevoie de alte setări,
compilează singur cu una dintre variantele de mai jos.

## Varianta A (recomandată pentru modificări): VS Code + PlatformIO

1. Instalează [Visual Studio Code](https://code.visualstudio.com/) și extensia **PlatformIO IDE**.
2. Clonează sau descarcă acest repository (butonul verde *Code → Download ZIP* pe GitHub).
3. În VS Code: *File → Open Folder…* → alege folderul **`firmware`**.
4. Așteaptă ca PlatformIO să descarce platforma ESP32 (prima dată durează câteva minute).
5. Apasă **✓ Build** (bara de jos), apoi **→ Upload**.

Sau din linia de comandă:

```bash
cd firmware
pio run                 # compilează
pio run -t upload       # încarcă pe placă
pio device monitor      # (opțional) monitor serial, 115200 baud
```

## Varianta B: Arduino IDE 2.x

1. *Tools → Board → Boards Manager*: instalează **„esp32 by Espressif Systems”**, versiunea **3.x**
   (placa Heltec V3 e inclusă în acest pachet, nu e nevoie de URL-uri suplimentare).
2. *Tools → Manage Libraries*: instalează
   - **HX711 Arduino Library** (Bogdan Necula)
   - **U8g2** (oliver / olikraus)
   - **ESP32Servo** (Kevin Harrington, John K. Bennett) – versiunea ≥ 3.0
3. Creează un folder numit `hanimandl` și copiază în el `firmware/src/hanimandl.cpp`
   redenumit **`hanimandl.ino`** (Arduino IDE cere ca fișierul să aibă numele folderului).
4. Deschide `hanimandl/hanimandl.ino`, alege *Tools → Board → esp32 → **Heltec WiFi Kit 32(V3)***,
   alege portul și apasă **Upload**.

## Dacă încărcarea nu pornește

- Ține apăsat butonul **PRG** de pe placă, apasă scurt **RST**, eliberează PRG, apoi reîncearcă upload-ul.
- Încearcă alt cablu / alt port USB.
- **Deconectează sursa externă de 5 V** cât timp placa e conectată prin USB la PC.

## Verificare după încărcare

Fără nimic conectat (doar placa pe USB) trebuie să vezi pe OLED: logo-ul cu albina + „HANI MANDL
v.0.2.13”, lista de autori, apoi **„Keine Waage!”** (= „Niciun cântar!”) – normal, HX711 încă nu e
legat. Asta confirmă că firmware-ul și ecranul funcționează.

---

## Setări opționale

Toate se fac în partea de sus a `hanimandl.cpp` (secțiunea *„Hier den Code auf die verwendete Hardware
einstellen”*):

| `#define` | Implicit | Când îl schimbi |
|-----------|----------|-----------------|
| `HARDWARE_LEVEL` | `3` | `3` = Heltec V3. `2` = Heltec V2 (alți pini, vezi mai jos). |
| `ROTARY_SCALE` | `2` | Pune `1` dacă encoderul sare câte 2 valori la un singur „clic” (ex. HW-040). |
| `SERVO_ERWEITERT` | activ | Interval puls servo 750–2500 µs. Dezactivează dacă servo-ul bate în capăt / bâzâie la 0°. |
| `QUETSCHHAHN_LINKS` | **activ** | Lasă-l activ pentru angrenajul Printables. Dezactivează doar la o mecanică cu braț direct. |
| `FEHLERKORREKTUR_WAAGE` | inactiv | Activează dacă greutatea afișată face salturi bruște (verifică întâi cablajul HX711). |
| `isDebug` | inactiv | `#define isDebug 4` pentru mesaje pe portul serial (depanare). |
| `MAXIMALGEWICHT` | `1000` | Cantitatea maximă selectabilă (g). Mărește pentru borcane > 1 kg. |

## Alte plăci

- **Heltec WiFi Kit 32 V2**: pune `HARDWARE_LEVEL 2` și în `platformio.ini`
  `board = heltec_wifi_kit_32_V2`. Pinii pentru V2 sunt în cod (blocul `#elif HARDWARE_LEVEL == 2`)
  și diferă complet de tabelul din [04-cablaj.md](04-cablaj.md).
- **ESP32 WROOM + ecran separat**: vezi fork-ul [RolandRust/HaniMandlWroom](https://github.com/RolandRust/HaniMandlWroom).
