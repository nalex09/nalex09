# Fișierele modelului 3D (Printables #524971)

**Autor:** rallef80 – <https://www.printables.com/model/524971-filling-machine-hanimandl>
**Licență:** GNU GPL v3 (aceeași ca firmware-ul, vezi [`../LICENSE`](../LICENSE))
**Versiune:** fișierele publicate pe 28.01.2026, descărcate de pe Printables pe 11.11.2026.

## Conținut

| Folder / fișier | Ce conține |
|-----------------|------------|
| [`stl/`](stl/) | piesele de printat (8 buc.) |
| [`step/`](step/) | aceleași piese în format STEP – pentru modificări în orice CAD |
| `hanimandl-rallef80.f3d` | proiectul complet Fusion 360 (asamblarea, cu toate componentele) |
| [`docs/parts-list.pdf`](docs/parts-list.pdf) | lista de componente a autorului (cu link-uri și prețuri, 07/2023) |
| [`docs/printables-524971-descriere.pdf`](docs/printables-524971-descriere.pdf) | descrierea de pe pagina modelului (EN/DE) |

## Piese de printat

| Fișier | Modul | Dimensiuni (mm) | Rol |
|--------|-------|-----------------|-----|
| `housing-upper-part.stl` | unitate de control | 130 × 88 × 25 | capacul: fereastră OLED, 2 găuri Ø12,5 (butoane), Ø7,4 (encoder), Ø20,5 (comutator rotund) |
| `housing-ground-part.stl` | unitate de control | 130 × 88 × 31 | cutia: gaură Ø8,2 (mufa DC), 2 × Ø6,1 (trecere cabluri cântar / servo) |
| `scale-ground-plate.stl` | cântar | 94 × 94 × 21 | baza: locaș celulă + HX711, 2 găuri Ø5,1 (M5) |
| `scale-top-plate.stl` | cântar | 104 × 104 × 12 | platforma: 2 găuri Ø4,1 (M4) spre celulă |
| `scale-topping-plate.stl` | cântar | 110 × 110 × 13 | capacul care se pune peste platformă (protejează șuruburile de miere) |
| `servo-mounting-plate.stl` | robinet | 159 × 98 × 12 | suportul servo, se prinde pe corpul robinetului |
| `gear-on-servo.stl` | robinet | 46 × 46 × 15 | roata dințată de pe servo (se înșurubează pe discul metalic 25T) |
| `gear-arm.stl` | robinet | 168 × 63 × 19 | brațul cu sector dințat, acționează robinetul |

Detalii de printare: [`../docs/02-printare-3d.md`](../docs/02-printare-3d.md).

## Unde merge fiecare șurub

Din lista autorului, corelată cu diametrele găurilor din fișierele STEP:

| Șurub | Buc. | Unde |
|-------|:----:|------|
| M5 × 20 cap înecat | 2 | celula de sarcină ↔ `scale-ground-plate` (găurile Ø5,1) |
| M4 × 20 cap înecat | 2 | celula de sarcină ↔ `scale-top-plate` (găurile Ø4,1) |
| M3 × 15 + șaibe | 5 | `gear-on-servo` ↔ discul metalic 25T al servo-ului |
| M3 × 20 + piuliță + șaibe | 2 | servo ↔ `servo-mounting-plate` |
| M3 × 30 + piuliță + șaibe | 1 | `gear-arm` (gaura Ø3) – lista îl numește „for the Servo Arm” |
| M6 × 50 | 1 | `gear-arm` (gaura Ø6) și `servo-mounting-plate` (găuri Ø6) – axul brațului* |

\* Lista autorului nu spune explicit unde merge M6 × 50; singurele găuri de Ø6 sunt în `gear-arm` și
`servo-mounting-plate`. Verifică în `hanimandl-rallef80.f3d` (Fusion 360 este gratuit pentru uz personal).
