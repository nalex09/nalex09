# 1. Lista de componente

> Autorul modelului a atașat pe Printables un **„Parts List” (PDF)** cu componentele pe care le-a folosit
> (tab-ul *Files* → *Other files*). Descarcă-l și verifică mai ales **dimensiunile celulei de sarcină și ale
> servo-ului** – piesele printate sunt făcute pe măsura lor. Lista de mai jos este cea standard pentru
> HaniMandl cu Heltec V3 și e compatibilă cu firmware-ul din acest repository.

## Electronică

| # | Componentă | Buc. | Note |
|---|------------|:----:|------|
| 1 | **Heltec WiFi Kit 32 V3** (ESP32-S3, OLED 0,96" integrat) | 1 | Firmware-ul e configurat pentru **V3**. Nu confunda cu „WiFi **LoRa** 32” (altă placă). Pentru V2 vezi [03-firmware.md](03-firmware.md#alte-plăci). |
| 2 | **Celulă de sarcină** tip bară, 2 kg sau 3 kg (format 80 × 12,7 × 12,7 mm) | 1 | Borcan 500 g plin ≈ 750–800 g, deci 2–3 kg e suficient și dă rezoluție bună. 5 kg merge și ea. |
| 3 | **Modul HX711** (amplificator 24 bit pentru celula de sarcină) | 1 | Se vinde de obicei la pachet cu celula. Alimentat la **3,3 V**. |
| 4 | **Servomotor** dimensiune standard, angrenaje metalice, ≥ 20 kg·cm (ex. **DS3218**, MG996R) | 1 | Robinetul strâns bine are nevoie de cuplu. DS3218 e alegerea mai sigură. Verifică în PDF-ul autorului ce servo încape în suport. |
| 5 | **Encoder rotativ cu buton** (modul KY-040) | 1 | `ROTARY_SCALE 2` în firmware. Pentru HW-040 vezi [03-firmware.md](03-firmware.md#setări-opționale). |
| 6 | **Comutator basculant 3 poziții ON-OFF-ON** | 1 | Automat / Manual / Setup. |
| 7 | **Buton cu revenire (NO), verde** | 1 | Start. |
| 8 | **Buton cu revenire (NO), roșu** | 1 | Stop / oprire de urgență. |
| 9 | **Buzzer activ** 3–5 V | 1 | Opțional (se activează din meniu). Trebuie să fie *activ* (piuie singur la tensiune), nu pasiv. |
| 10 | **Sursă 5 V / min. 3 A** + mufă DC (tată/mamă) | 1 | Alimentează placa și servo-ul. Servo-ul trage vârfuri de 2–3 A. |
| 11 | Conectori pentru cablurile dintre module (ex. GX12 / GX16 aviație, 3–4 pini) | 3 perechi | Unitate control ↔ cântar (4 fire), ↔ servo (3 fire), alimentare. Se pot și lipi direct. |
| 12 | Fire (ex. 0,25 mm² / AWG24), termocontractabil, pini header 2,54 mm | – | Pentru servo folosește fire mai groase pe + și GND. |
| 13 | Opțional: condensator electrolitic 470–1000 µF / 10 V | 1 | Pus între 5 V și GND lângă servo, reduce resetările la pornirea servo-ului. |

## Mecanică

| # | Componentă | Buc. | Note |
|---|------------|:----:|------|
| 1 | **Maturator / vas de îmbuteliere cu robinet standard de plastic** (în germană „Quetschhahn”) | 1 | Mecanismul printat se prinde pe robinet. |
| 2 | Șuruburi pentru celula de sarcină | 4 | De regulă 2 × M4 + 2 × M5 (verifică filetele celulei tale), lungimea în funcție de grosimea pieselor printate. |
| 3 | Șuruburi pentru servo + suport servo | ~4–6 | Cele livrate cu servo-ul + ce cere modelul. |
| 4 | Adeziv cianoacrilat (superglue) | – | Placa Heltec se lipește în capacul unității de control (versiunea 11/2023 a carcasei). |
| 5 | Filament **PLA** | ~0,5 kg | Autorul a printat totul în PLA. |
| 6 | Greutate de calibrare cunoscută (ex. 500 g) | 1 | Poate fi și un borcan plin cântărit pe un cântar de bucătărie bun. |

## Ce să verifici înainte de a comanda

- **Heltec V3** are pinii diferiți față de V1/V2 – tot ghidul (cablaj + firmware) e pentru **V3**.
- Celula de sarcină trebuie să intre în piesa de jos a cântarului printat – verifică dimensiunile în
  fișierul Fusion 360 / STL înainte de comandă.
- Servo-ul trebuie să intre în suportul printat (format standard ~40 × 20 mm).
