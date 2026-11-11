# 1. Lista de componente

Aceasta este **lista autorului modelului** ([`hardware/docs/parts-list.pdf`](../hardware/docs/parts-list.pdf),
prețuri Amazon.de / eBay.de din 12.07.2023). Piesele printate sunt făcute pe măsura acestor componente,
deci e bine să le iei pe acestea sau unele cu **aceleași dimensiuni**. Total ≈ **77 €** pentru o mașină.

## Electronică

| # | Componentă (cum apare în listă) | Buc. | Note |
|---|---------------------------------|:----:|------|
| 1 | **Heltec WiFi Kit 32** – ESP32 cu OLED 0,96" | 1 | Ia versiunea **V3** (firmware-ul și cablajul din acest repo sunt pentru V3). **Atenție: varianta WiFi, nu cea cu LoRa!** |
| 2 | **Encoder rotativ KY-040** | 1 | Se vinde la set de 5. Filet ax 7 mm (gaura din capac Ø7,4). |
| 3 | **Servo digital 20 kg, 270°** (Miuzei) | 1 | Format standard. Vezi nota despre 270° mai jos. |
| 4 | **Disc metalic pentru servo, 25T** (diymore) | 1 | Roata dințată printată se înșurubează pe el. Trebuie să fie **25T** (canelura servo-ului de 20 kg). |
| 5 | **Celulă de sarcină 1 kg + modul HX711** | 1 | Bară standard ~80 × 12,7 × 12,7 mm cu filete M4 și M5. |
| 6 | **Buton 12 mm, impermeabil**, cu revenire | 2 | Unul verde (START), unul roșu (STOP). Gaura din capac: Ø12,5. Trebuie să fie *momentary* (cu revenire), contact normal deschis. |
| 7 | **Comutator basculant rotund Ø20 mm** | 1 | Trebuie să fie cu **3 poziții (ON-OFF-ON)**. Gaura din capac: Ø20,5. |
| 8 | **Mufă DC mamă 5,5 × 2,1 mm** pentru panou | 1 | Gaura din cutie: Ø8,2. |
| 9 | **Sursă 5 V / 3 A**, mufă 5,5 × 2,1 mm | 1 | Alimentează placa și servo-ul. |

Nu sunt în lista autorului, dar îți trebuie / sunt utile:

| Componentă | Note |
|------------|------|
| Fire (ex. 0,25 mm²), termocontractabil, fludor | Cablurile spre cântar și servo ies prin cele 2 găuri Ø6 din cutie (autorul nu folosește conectori). |
| Cablu USB-C **de date** | Pentru programarea plăcii. |
| Buzzer activ 3–5 V *(opțional)* | Nu are loc dedicat în carcasă; se poate lipi în interior. Firmware-ul merge și fără. |
| Condensator 470–1000 µF / 10 V *(opțional)* | Între 5 V și GND la servo, previne resetările. |

### Despre servo-ul de 270°

Firmware-ul comandă servo-ul cu impulsuri de 750–2500 µs pe o scară „0–180”. Pe un servo de 270°
asta acoperă aproximativ 230–240° reali, deci **unghiurile din meniu nu sunt grade reale** – nu
contează, pentru că valorile Minimum / Feindos. / Maximum se reglează oricum după robinet
([06-calibrare-utilizare.md](06-calibrare-utilizare.md)). Cu angrenajul cu roți dințate, cursa mare
permite deschiderea completă a robinetului.

### Despre celula de 1 kg

Cântarul trebuie să ducă borcanul **plin**. Un borcan de 500 g cântărește plin ≈ 700–800 g, deci 1 kg
ajunge pentru borcane de până la 500 g. Pentru borcane de 1 kg ia o celulă de **2 kg** în același format
(de obicei aceleași dimensiuni și filete) și mărește `MAXIMALGEWICHT` în firmware.

## Mecanică

| # | Componentă | Buc. | Unde |
|---|------------|:----:|------|
| 1 | **Robinet de plastic Imgut® „Plastik-Quetschhahn”** (pe maturator / găleată de îmbuteliere) | 1 | Suportul servo și brațul sunt făcute pe forma acestui robinet. Alt model de robinet probabil cere modificarea pieselor (proiectul Fusion e inclus). |
| 2 | Șurub M6 × 50 | 1 | brațul cu sector dințat (vezi [`hardware/README.md`](../hardware/README.md#unde-merge-fiecare-șurub)) |
| 3 | Șurub M5 × 20 cap înecat | 2 | celulă ↔ baza cântarului |
| 4 | Șurub M4 × 20 cap înecat | 2 | celulă ↔ platforma cântarului |
| 5 | Șurub M3 × 30 + piuliță + șaibe | 1 | brațul (`gear-arm`) |
| 6 | Șurub M3 × 20 + piuliță + șaibe | 2 | servo ↔ suport servo |
| 7 | Șurub M3 × 15 + șaibe | 5 | roata dințată ↔ discul metalic al servo-ului |
| 8 | Adeziv cianoacrilat (superglue) | – | fixează placa Heltec în capacul unității de control |
| 9 | Filament **PLA** | ~0,3 kg | toate piesele (vezi [02-printare-3d.md](02-printare-3d.md)) |
| 10 | Greutate cunoscută pentru calibrare (ex. 500 g) | 1 | poate fi un obiect cântărit pe un cântar bun |

Autorul recomandă un set de șuruburi M3 inox cu piulițe (570 buc.) – mai ieftin decât bucăți separate.

## Unde găsești în România

Componentele electronice sunt standard (eMAG, Optimus Digital, Sigmanortec, AliExpress etc.). Caută după:
„Heltec WiFi Kit 32 V3”, „KY-040”, „servo 20kg 270 grade”, „disc metalic servo 25T”,
„celula de sarcina 1kg HX711”, „buton 12mm impermeabil”, „comutator basculant rotund 20mm ON-OFF-ON”.
Robinetul Imgut se găsește la magazinele germane de apicultură (ex. Holtermann – link în PDF);
verifică dacă robinetul maturatorului tău are aceeași formă înainte să printezi.
