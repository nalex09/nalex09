# Plan de lucru – pas cu pas

Bifează pe măsură ce termini. Fiecare etapă are un **„Gata când”** – nu trece mai departe până nu e
îndeplinit. Ordinea e gândită ca să **nu strici nimic** și să descoperi problemele cât mai devreme,
când sunt ușor de reparat.

Timp total estimat: **2–3 weekenduri** de lucru efectiv (+ așteptarea coletelor).

---

## Etapa 0 – Verificări înainte de a cumpăra ceva (1 oră)

- [ ] Uită-te la robinetul maturatorului tău. Modelul e făcut pentru **robinetul de plastic Imgut**
      („Quetschhahn”). Compară cu pozele de pe Printables și măsoară diametrul corpului robinetului
      (suportul servo are un arc de ~54,5 mm).
- [ ] Dacă ai imprimantă 3D: printează **doar `servo-mounting-plate.stl`** (~2–3 ore) și probează-l pe robinet.
- [ ] Verifică ce unelte ai (vezi lista de la Etapa 1).

**Gata când:** știi că suportul se potrivește pe robinetul tău (sau ai decis să cumperi robinetul Imgut).

> Dacă robinetul tău e diferit, ai două variante: cumperi un robinet Imgut (~10 €) sau adaptezi
> piesele în Fusion 360 (`hardware/hanimandl-rallef80.f3d`). Prima e mult mai simplă.

---

## Etapa 1 – Comandă componentele (30 min + așteptare)

Lista completă: [01-componente.md](01-componente.md). Pe scurt:

- [ ] Heltec **WiFi Kit 32 V3** (nu LoRa!)
- [ ] Celulă de sarcină **2 kg** + HX711 (format 80 × 12,7 × 12,7 mm, filete M4 + M5)
- [ ] Servo 20 kg 270° + **disc metalic 25T**
- [ ] Encoder KY-040
- [ ] 2 butoane 12 mm cu revenire (verde + roșu)
- [ ] Comutator basculant rotund Ø20 mm, **3 poziții ON-OFF-ON**
- [ ] Mufă DC panou 5,5 × 2,1 mm + sursă 5 V / 3 A
- [ ] Șuruburi: 2 × M5×20 și 2 × M4×20 cap înecat, 1 × M6×50, set M3 (×15, ×20, ×30 + piulițe + șaibe)
- [ ] Robinet Imgut (dacă e cazul)
- [ ] Mărunțișuri: fire, termocontractabil, fire Dupont mamă-mamă (pentru teste), cablu USB-C de date
- [ ] Opțional: buzzer activ, condensator 1000 µF / 10 V

Unelte necesare: ciocan de lipit + fludor, multimetru, șurubelnițe, cleşte de tăiat/dezizolat,
superglue, imprimantă 3D (sau pe cineva care printează pentru tine), un obiect cu greutate cunoscută
(ex. 1 kg zahăr nedeschis – mai bine cântărit pe un cântar de bucătărie bun).

**Gata când:** totul e comandat.

---

## Etapa 2 – Printare (cât aștepți coletele, ~15–20 ore de imprimantă)

Setări și orientare: [02-printare-3d.md](02-printare-3d.md). În această ordine:

- [ ] `servo-mounting-plate` (dacă nu l-ai printat la Etapa 0)
- [ ] `gear-on-servo` și `gear-arm` – solide, strat fin
- [ ] `scale-ground-plate`, `scale-top-plate`, `scale-topping-plate`
- [ ] `housing-ground-part`, `housing-upper-part`

**Gata când:** toate cele 8 piese sunt printate, găurile curate (dă cu un burghiu de mână dacă sunt strâmte).

---

## Etapa 3 – Firmware pe placă (30 min, imediat ce vine Heltec-ul)

Ghid: [03-firmware.md](03-firmware.md) – „Varianta rapidă” din browser.

- [ ] Conectează placa la PC cu USB-C (fără nimic altceva legat).
- [ ] Încarcă `firmware/bin/hanimandl-v0.2.13-heltec-v3-factory.bin` la adresa `0x0` cu
      <https://espressif.github.io/esptool-js/> (Chrome / Edge).
- [ ] Apasă RST.

**Gata când:** pe ecran apare albina + „HANI MANDL v.0.2.13”, apoi **„Keine Waage!”**
(= niciun cântar – normal, încă nu l-ai legat).

---

## Etapa 4 – Test pe masă, câte o componentă (2–3 ore)

Cablaj: [04-cablaj.md](04-cablaj.md). Lipește pinii header pe Heltec (dacă nu sunt lipiți) și leagă
provizoriu cu fire Dupont. **Adaugă câte o componentă, testează, apoi treci la următoarea.**
Deconectează USB-ul de fiecare dată când legi ceva.

- [ ] **Comutatorul** (pinii 40 / 41 / 42) → pornește placa: pozițiile schimbă ecranul între
      *Automatik*, ecranul manual și *Setup*. Dacă Automatik ↔ Setup sunt inversate, schimbă firele 40/42.
- [ ] **Encoderul** (47 / 48 / 26, + la 3V3) → în Setup, rotirea mută selecția, apăsarea intră în meniu.
- [ ] **Butoanele** (START 6/7, STOP 4/5) → în modul manual, verde afișează ▶, roșu ⏸.
- [ ] **HX711 + celula de 2 kg** (39 / 38, VCC la **3V3**) → mesajul „Keine Waage!” dispare.
      Ține celula fixată de un capăt pe masă, apasă ușor celălalt capăt: numărul se schimbă.
      Dacă scade în loc să crească, inversează A+ cu A−.
- [ ] **Servo-ul** (semnal 33, + și − din sursa de **5 V**, GND comun) – **fără nimic montat pe ax**.
      Alimentează din sursa de 5 V (scoate USB-ul). În modul manual: verde, apoi rotește encoderul → servo-ul se rotește.
- [ ] Opțional: **buzzer** (pin 2) + Setup → Parameter → Buzzer ein.

**Gata când:** toate componentele răspund corect, iar placa nu se resetează când se mișcă servo-ul.

---

## Etapa 5 – Cântarul (1 oră)

Ghid: [05-asamblare.md](05-asamblare.md#52-cântarul).

- [ ] Celula în bază cu 2 × M5×20, platforma pe celulă cu 2 × M4×20. HX711 în bază.
- [ ] Verifică: platforma nu atinge baza nicăieri (trece o foaie de hârtie prin jur).
- [ ] Pornește, așteaptă 3 minute, apoi **Setup → Kalibrieren** cu greutatea cunoscută
      (rotește encoderul ca să setezi valoarea, ex. 1000 g).
- [ ] Verifică în modul manual cu 2–3 obiecte cântărite pe alt cântar.

**Gata când:** cântarul arată corect (± 1–2 g) și revine la 0 când îl golești.

---

## Etapa 6 – Unitatea de control (2–4 ore)

Ghid: [05-asamblare.md](05-asamblare.md#53-unitatea-de-control).

- [ ] Montează în capac: encoderul, butoanele, comutatorul.
- [ ] Lipește placa Heltec în locaș cu superglue (fără adeziv pe butoane / mufa USB).
- [ ] Înlocuiește firele Dupont cu fire lipite (izolează fiecare lipitură cu termocontractabil).
- [ ] În cutie: mufa DC; cablurile spre cântar și servo prin cele 2 găuri Ø6 (cu nod de siguranță).
- [ ] **Refă testul de la Etapa 4** (comutator, encoder, butoane, cântar, servo) înainte să închizi cutia.
- [ ] Închide cutia (se îmbină prin presare).

**Gata când:** totul funcționează cu cutia închisă, alimentat din sursa de 5 V.

---

## Etapa 7 – Mecanismul robinetului (1–2 ore)

Ghid: [05-asamblare.md](05-asamblare.md#54-mecanismul-robinetului-servo--roți-dințate).
**Maturatorul gol** la acest pas!

- [ ] Suportul pe robinet, servo-ul în suport (2 × M3×20).
- [ ] Roata dințată pe discul metalic 25T (5 × M3×15) – **discul încă nu pe servo**.
- [ ] Brațul `gear-arm` pe robinet (M3×30, M6×50).
- [ ] Pornește electronica → servo-ul merge în poziția „închis”.
- [ ] Închide robinetul de mână, pune discul cu roata pe ax ca dinții să se prindă, strânge șurubul central.
- [ ] Mod manual → verde → rotește încet encoderul: robinetul trebuie să se **deschidă**.
- [ ] Notează `W=` pentru: închis etanș (**Minimum**), fir subțire (**Feindos.**), deschis complet (**Maximum**).
- [ ] Setup → **Servoeinst.** → introdu valorile → Speichern.

**Gata când:** robinetul se închide etanș și se deschide complet fără ca servo-ul să bâzâie/forțeze în capete.

---

## Etapa 8 – Configurarea umplerii (30 min)

Ghid: [06-calibrare-utilizare.md](06-calibrare-utilizare.md).

- [ ] Setup → **Füllmenge**: setează borcanele tale (ex. 250 g, 500 g, 1000 g).
- [ ] Setup → **Tarawerte**: pentru fiecare, pune borcanul gol și apasă OK
      (**obligatoriu** – fără tară modul Automat nu pornește).
- [ ] Setup → **Korrektur**: începe cu `-5`.
- [ ] Setup → **Automatik**: Autostart *aus* deocamdată.

**Gata când:** pentru fiecare cantitate ai tara setată (nu mai apare „fehlt”).

---

## Etapa 9 – Probe cu apă, apoi cu miere

- [ ] Pune **apă** în maturator. Mod Automatik, borcan gol, verde → se umple și se oprește.
- [ ] Cântărește borcanul pe alt cântar. Ajustează **Korrektur** (mai negativ dacă iese prea plin).
- [ ] Repetă până iese corect de 3 ori la rând.
- [ ] Treci la **miere**: Korrektur și **Feindos.** se reglează din nou (mierea e mult mai vâscoasă).
- [ ] Activează **Autostart** și **Autokorr.** (cu Kulanz 2–5 g) când ești mulțumit.

**Gata când:** umpli 10 borcane la rând fără intervenție, toate la greutatea dorită sau puțin peste. 🍯

---

Ceva nu merge? → [07-depanare.md](07-depanare.md)
