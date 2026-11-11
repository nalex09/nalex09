# 2. Printarea pieselor 3D

Fișierele sunt pe Printables: <https://www.printables.com/model/524971-filling-machine-hanimandl/files>
(butonul **Download → All model files**). Pachetul conține STL-urile și proiectul **Fusion 360 (.f3d)**,
util dacă vrei să muți butoanele sau să adaptezi suporturile la alte componente.

## Piese

| Modul | Piese | Observații |
|-------|-------|------------|
| **Unitate de control** | carcasă – partea de sus, carcasă – partea de jos | Cele două părți se îmbină prin presare, fără șuruburi. Din 11/2023 partea de sus e simplificată: placa Heltec se așază în locaș și se fixează cu superglue. |
| **Cântar** | partea de jos (suportul celulei + HX711), placa de sus (prinsă cu șuruburi de celulă), capac de protecție | Capacul se pune peste placa de sus ca mierea să nu picure pe șuruburi. |
| **Mecanism robinet** | suport servo (se prinde fix de robinet), roată dințată pentru robinet, roată dințată / braț pentru servo | Folosește cea mai nouă versiune a roții robinetului (ex. „hahn-zahnrad-v106”) dacă sunt mai multe variante. |

## Setări de printare recomandate

Autorul a printat **totul în PLA**. Setări uzuale care funcționează bine:

| Setare | Carcase / cântar | Roți dințate / suport servo |
|--------|------------------|------------------------------|
| Înălțime strat | 0,2 mm | 0,12–0,16 mm (dinți mai preciși) |
| Pereți (perimetre) | 3 | 4–5 |
| Umplere | 15–20 % | 40–100 % |
| Suporturi | doar unde slicer-ul indică surplombe mari | în general nu |

Sfaturi:

- Roțile dințate și suportul servo preiau tot cuplul servo-ului – printează-le solid (mulți pereți,
  umplere mare). PETG este o alternativă mai rezistentă la căldură dacă atelierul e cald vara.
- Verifică ajustajul roții pe maneta robinetului înainte de a printa restul; dacă e prea strâns/larg,
  scalează ușor piesa în slicer (ex. 100,5 % / 99,5 %) sau modific-o în Fusion.
- Piesele nu stau în contact direct cu mierea (doar eventuale picături pe capacul cântarului), dar
  păstrează-le curate; PLA nu suportă spălarea la apă fierbinte.
