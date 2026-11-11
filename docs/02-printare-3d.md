# 2. Printarea pieselor 3D

Toate fișierele sunt în repo, în [`hardware/stl/`](../hardware/stl/) (8 piese). Pentru modificări:
[`hardware/step/`](../hardware/step/) sau proiectul Fusion 360 `hardware/hanimandl-rallef80.f3d`.
Autorul a printat **totul în PLA**. Consum estimat: **~250–300 g** de filament. Cea mai mare piesă are
168 mm, deci încape pe orice imprimantă cu masa de minim 180 × 180 mm.

## Piese și orientare pe masă

Unele STL-uri sunt exportate cu fața plată mare **în sus**. Întoarce-le ca să stea pe fața mare
(PrusaSlicer: tasta **F** / *Place on face*; Cura: *Lay flat* / *Select face to align to build plate*):

| Fișier | Dimensiuni (mm) | Orientare | Setări recomandate |
|--------|-----------------|-----------|--------------------|
| `housing-ground-part.stl` | 130 × 88 × 31 | așa cum e | 3 pereți, 15–20 % |
| `housing-upper-part.stl` | 130 × 88 × 25 | **întoarce-o** (fața de sus a capacului pe masă) | 3 pereți, 15–20 % |
| `scale-ground-plate.stl` | 94 × 94 × 21 | **întoarce-o** (fața plată pe masă) | 4 pereți, 30 % |
| `scale-top-plate.stl` | 104 × 104 × 12 | **întoarce-o** (fața plată pe masă) | 4 pereți, 30 % |
| `scale-topping-plate.stl` | 110 × 110 × 13 | **întoarce-o** (fața plată pe masă) | 3 pereți, 15 % |
| `servo-mounting-plate.stl` | 159 × 98 × 12 | **culcă-o** pe fața mare de 159 × 98 (exportată în picioare) | 5 pereți, 50 % |
| `gear-on-servo.stl` | 46 × 46 × 15 | așa cum e | 5 pereți, 60–100 %, strat 0,12–0,16 mm |
| `gear-arm.stl` | 168 × 63 × 19 | așa cum e | 5 pereți, 50–100 %, strat 0,12–0,16 mm |

Setări generale: strat 0,2 mm (piesele cu dinți 0,12–0,16 mm pentru precizie), fără suporturi
în orientările de mai sus (dacă slicer-ul semnalează surplombe mari, activează suporturi doar pe masă).

## Sfaturi

- **Roțile dințate și suportul servo** preiau tot cuplul servo-ului de 20 kg – printează-le solid.
  PETG e o alternativă mai rezistentă dacă atelierul e cald vara.
- Verifică pe primele straturi că găurile ies corect; la nevoie folosește *hole compensation* /
  *XY compensation* în slicer. Diametrele din model: M3 → Ø3,2, M4 → Ø4,1, M5 → Ø5,1, M6 → Ø6,0.
- Printează mai întâi `servo-mounting-plate` și probează-l pe robinetul tău (arcul de prindere are
  Ø ~54,5 mm, făcut pentru robinetul **Imgut**). Dacă nu se potrivește, modifică în Fusion/STEP
  înainte să printezi restul mecanismului.
- Piesele nu stau în contact direct cu mierea (doar eventuale picături pe capacul cântarului).
  PLA nu suportă apa fierbinte – curăță cu apă călduță.
