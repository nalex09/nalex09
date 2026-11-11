# 6. Calibrare, setări și utilizare

Meniurile de pe ecran sunt în **germană** (firmware-ul original). Glosarul de la final traduce tot.

## Comenzi

| Element | Funcție |
|---------|---------|
| **Comutator 3 poziții** | **Automatik** (automat) · mijloc = **Handbetrieb** (manual) · **Setup** |
| **Encoder (rotire)** | navigare în meniu / modificare valoare / unghi robinet |
| **Encoder (apăsare)** | **OK** – selectare, confirmare; în manual = tara |
| **Buton verde** | START – activează servo-ul / pornește umplerea |
| **Buton roșu** | STOP – închide imediat robinetul; în Setup iese din submeniu |

## 6.1 Prima configurare (în ordinea asta)

Pune comutatorul pe **Setup**. Meniul (rotativ) conține:
`Tarawerte · Kalibrieren · Korrektur · Füllmenge · Automatik · Servoeinst. · Parameter · Zählwerk · ZählwerkTrip · Clear Prefs`

### Pasul 1 – Kalibrieren (calibrarea cântarului)

1. Alege **Kalibrieren** → OK.
2. Ecran: *„Bitte Waage leeren und mit OK bestätigen”* → golește cântarul, apasă **OK**.
3. Ecran: *„Bitte 500g aufstellen …”* → rotește encoderul ca să setezi greutatea de calibrare pe care o ai
   (100–9999 g), pune-o pe cântar, apasă **OK**.
4. Valoarea se salvează permanent. Verifică cu un obiect cunoscut în modul Manual.

> Lasă electronica pornită 2–3 minute înainte de calibrare – HX711 și celula se încălzesc ușor și
> citirea se stabilizează.

### Pasul 2 – Servoeinst. / Servowinkel (unghiurile robinetului)

Valorile le-ai notat la asamblare ([05-asamblare.md](05-asamblare.md#54-mecanismul-robinetului-servo--roți-dințate)).

| Linie | Ce înseamnă |
|-------|-------------|
| `Livesetup ein/aus` | cu `ein`, servo-ul se mișcă în timp ce reglezi – vezi direct efectul (atenție dacă maturatorul e plin!) |
| `Minimum` | robinet **închis etanș** (cât mai puțin forțat) |
| `Feindos.` | unghiul de **dozare fină** – fir subțire spre final. Mai mare = umplere mai rapidă, mai mic = mai precis |
| `Maximum` | robinet **deschis complet** (limita mecanicii) |
| `Speichern` | salvează |

### Pasul 3 – Füllmenge (cantitățile)

Sunt 5 poziții de borcan. Pentru fiecare setezi **greutatea netă** (ex. 250 g, 500 g) și **tipul de
borcan** (`DIB`, `TOF`, `DEE` – doar o etichetă, alege ce vrei). Pașii de reglaj se măresc automat
(1 g → 5 g → 25 g …) ca să ajungi repede la valori mari.

### Pasul 4 – Tarawerte (tara fiecărui tip de borcan)

1. Alege cantitatea/borcanul din listă, pune **borcanul gol** pe cântar, apasă **OK**.
2. Repetă pentru fiecare tip. Unde scrie `fehlt` (lipsește), tara nu e încă setată.

> **Obligatoriu:** fără tară setată pentru cantitatea aleasă, **modul Automat nu pornește** (butonul verde
> nu are efect). Tot după tară recunoaște mașina „borcanul gol potrivit” la Autostart.

### Pasul 5 – Korrektur (corecția)

Mierea mai curge puțin după ce robinetul se închide. Corecția (−90 … +20 g) mută punctul de
închidere: valoare **negativă** = închide mai devreme. Începe cu `-5`, fă câteva borcane de probă și
ajustează până ajungi la greutatea dorită. Corecția depinde de temperatura și vâscozitatea mierii.

### Pasul 6 – Automatik

| Linie | Ce înseamnă |
|-------|-------------|
| `Autostart ein/aus` | pornește singur când pui un borcan gol potrivit (vezi mai jos) |
| `Glastol. ±20g` | cât poate varia greutatea borcanului gol față de tara salvată |
| `Autokorr. ein/aus` | autocorecție: ajustează corecția singur, borcan cu borcan, pe măsură ce scade nivelul (și presiunea) în maturator |
| `-> Kulanz 2g` | surplusul voit la autocorecție (borcanul să nu iasă **sub** greutatea de pe etichetă) |
| `Speichern` | salvează |

### Pasul 7 – Parameter

- `Buzzer ein/aus` – semnale sonore (implicit **oprit**!). Activează-l dacă ai montat buzzer.
- `Menu Liste/Scroll` – aspectul meniului Setup.

### Alte meniuri

- **Zählwerk** – contor total de borcane și kilograme umplute (pe tip de borcan).
- **ZählwerkTrip** – contor parțial, se poate reseta (ex. pe sezon / pe lot).
- **Clear Prefs** – șterge **toate** setările (inclusiv calibrarea). Cere confirmare.

## 6.2 Mod Manual (Handbetrieb)

Comutatorul pe mijloc.

- **Verde** activează servo-ul (▶), **roșu** îl dezactivează (⏸) și închide robinetul.
- Rotind encoderul deschizi robinetul (procent + unghi `W=` sus pe ecran).
- **Apăsare encoder** = tara (cântarul arată 0 cu ce e pe el); apasă din nou cu cântarul gol ca să revii.

Util pentru umplere manuală, pentru a găsi unghiurile servo și pentru a verifica calibrarea.

## 6.3 Mod Automat (Automatik)

Comutatorul pe **Automatik**. Linia de jos arată corecția (`k=` sau `ak=` cu autocorecție) și
cantitatea aleasă; sus apare `AS` dacă Autostart e activ.

- Cu robinetul închis, **apasă encoderul** ca să alegi ce modifici (corecția sau cantitatea – valoarea
  clipește), apoi rotește.
- **Verde** = pornire. **Roșu** = oprire de urgență (închide robinetul și oprește automatul).
- Rotirea encoderului în timpul umplerii limitează deschiderea maximă.

**Fără Autostart (semi-automat):** pui borcanul, apeși verde → se umple până la cantitatea setată și se
oprește. Pentru următorul borcan apeși din nou verde. *Atenție:* umple și borcane începute – un borcan
de 125 g pe jumătate plin poate porni o umplere de 500 g.

**Cu Autostart (automat complet):** apeși verde o dată (▶). Pune un borcan gol care corespunde tarei
(± toleranța) – după ~1,5 s stabil apare `START` și umplerea pornește. Iei borcanul plin, pui altul gol,
și ciclul se repetă singur. Un borcan început **nu** pornește automat; apasă verde ca să forțezi.

## 6.4 Sfaturi practice

- Mierea caldă (dar sub 40 °C) curge uniform și dă rezultate mai constante.
- Fă primele teste cu **apă** sau sirop – mai ieftin decât mierea vărsată.
- Verifică periodic cu un cântar de control; ajustează corecția sau lasă autocorecția să lucreze.
- Curăță capacul cântarului de picături – greutatea lor intră în măsurătoare.

---

## Glosar ecran (germană → română)

| Pe ecran | Înseamnă |
|----------|----------|
| Handbetrieb | mod manual |
| Automatik | mod automat |
| Setup | configurare |
| Tara / Tarawerte | tara / valorile de tară (greutatea borcanului gol) |
| Kalibrieren | calibrare |
| Korrektur (`k=`) | corecție |
| Autokorrektur / Autokorr. (`ak=`) | autocorecție |
| Kulanz | surplus voit (toleranță în plus) |
| Füllmenge | cantitate de umplere |
| Glastol. (Glastoleranz) | toleranța greutății borcanului |
| Autostart (`AS`) | pornire automată |
| Servowinkel / Servoeinst. | unghiuri servo / setări servo |
| `W=` | unghiul (Winkel) curent al servo-ului |
| Feindos. (Feindosierung) | dozare fină |
| Minimum / Maximum | minim / maxim |
| Livesetup | reglaj în timp real |
| Parameter | parametri |
| Zähler / Zählwerk | contor |
| Zähler Trip / ZählwerkTrip | contor parțial (resetabil) |
| Summe / Gesamt | total |
| St. (Stück) | buc. |
| Gewicht / Zielgewicht | greutate / greutate țintă |
| Nachtropfen | picurare după închidere |
| Speichern | salvează |
| Abbrechen | anulează |
| Löschen / Clear Prefs | șterge / șterge toate setările |
| Zurück! | înapoi! |
| OK | OK |
| ein / aus | pornit / oprit |
| fehlt | lipsește |
| alter Wert / vorher | valoarea veche / anterior |
| Bitte Waage leeren | golește cântarul |
| und mit OK bestätigen | și confirmă cu OK |
| Bitte 500g aufstellen | pune 500 g pe cântar |
| Bitte Glas aufstellen | pune borcanul |
| Keine Waage! | niciun cântar detectat |
| Nicht kalibr. | cântar necalibrat |
| Waage leeren! | golește cântarul! (la pornire era ceva pe el) |
| START | pornire (borcan detectat) |
| DIB / TOF / DEE | tipuri de borcan: *Deutscher Imkerbund* / *Twist-Off* / *DeepTwist* |
