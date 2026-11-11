# HaniMandl – mașină semi-automată de îmbuteliat miere

Implementare a proiectului **[Filling machine „Hanimandl” (Printables #524971)](https://www.printables.com/model/524971-filling-machine-hanimandl)**
de *rallef80*: o mașină care umple borcane cu o cantitate exactă (ex. 250 g sau 500 g) de miere
(sau alte lichide vâscoase), acționând robinetul standard de plastic al maturatorului cu un servomotor
prin **roți dințate**.

Firmware-ul este **[HaniMandl](https://github.com/hiveeyes/hanimandl)** (v0.2.13, comunitatea Hiveeyes),
pregătit aici pentru placa **Heltec WiFi Kit 32 V3** și pentru mecanica cu roți dințate de pe Printables.

Mașina are trei module, legate prin cabluri:

1. **Unitatea de control** – placa Heltec WiFi Kit 32 V3 (ESP32-S3 cu ecran OLED), encoder rotativ,
   buton verde (start), buton roșu (stop), comutator cu 3 poziții (Automat / Manual / Setup), buzzer.
2. **Cântarul** – celulă de sarcină + modul HX711, pe care stă borcanul sub robinet.
3. **Mecanismul robinetului** – servomotor montat direct pe robinetul maturatorului, care rotește
   robinetul prin două roți dințate (deschidere completă, cuplu maxim în orice poziție).

## Cum funcționează

1. Pui un borcan gol pe cântar.
2. Mașina face tara, deschide robinetul complet, apoi îl închide treptat pe măsură ce se apropie de
   greutatea țintă (dozare fină).
3. Închide robinetul la greutatea setată (+ corecție pentru mierea care mai curge după închidere).
4. Cu *Autostart* activ, pornește singură la următorul borcan gol.

## Pașii de implementare

| # | Etapă | Document |
|---|-------|----------|
| 1 | Cumpără componentele | [docs/01-componente.md](docs/01-componente.md) |
| 2 | Printează piesele 3D | [docs/02-printare-3d.md](docs/02-printare-3d.md) |
| 3 | Încarcă firmware-ul pe Heltec V3 | [docs/03-firmware.md](docs/03-firmware.md) |
| 4 | Fă cablajul | [docs/04-cablaj.md](docs/04-cablaj.md) |
| 5 | Asamblează mecanica | [docs/05-asamblare.md](docs/05-asamblare.md) |
| 6 | Calibrează și folosește mașina (+ glosar meniuri DE→RO) | [docs/06-calibrare-utilizare.md](docs/06-calibrare-utilizare.md) |
| 7 | Depanare | [docs/07-depanare.md](docs/07-depanare.md) |

> **Recomandare de ordine:** încarcă firmware-ul (pasul 3) și testează electronica pe masă
> **înainte** de a monta totul în carcase. Servo-ul se cuplează la robinet **doar după** prima
> pornire (servo-ul se duce singur în poziția „închis”).

## Structura repository-ului

```
firmware/
  platformio.ini        configurația PlatformIO (Heltec WiFi Kit 32 V3)
  src/hanimandl.cpp     firmware HaniMandl v0.2.13 (cu QUETSCHHAHN_LINKS activat)
  bin/                  firmware gata compilat (se încarcă din browser, la adresa 0x0)
  UPSTREAM.md           de unde provine codul și ce s-a modificat
docs/                   ghidul de construcție, pas cu pas (în română)
.github/workflows/      compilare automată a firmware-ului la fiecare push
```

## Licență și credite

- Firmware: © Marc Vasterling, Marc Wetzel, Clemens Gruber, Marc Junker, Andreas Holzhammer,
  Johannes Kuder, Jeremias Bruker, Joshua Schumacher – [hiveeyes/hanimandl](https://github.com/hiveeyes/hanimandl), **GPLv3** (vezi [LICENSE](LICENSE)).
- Modelul 3D (carcase, cântar, angrenaj robinet): *rallef80* – [Printables #524971](https://www.printables.com/model/524971-filling-machine-hanimandl), **GPLv3**.
  Fișierele STL / Fusion 360 nu sunt copiate aici; descarcă-le de pe Printables.
- Comunitate: [forumul Hiveeyes (DE)](https://community.hiveeyes.org/t/hanimandl-halbautomatischer-honig-abfull-roboter/768),
  [documentația HaniMandl](https://hanimandl.readthedocs.io/).
