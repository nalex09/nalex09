# 5. Asamblare

Ordinea recomandată: **electronica testată pe masă → cântar → unitate de control → mecanism robinet**.

## 5.1 Test pe masă (înainte de carcase)

1. Încarcă firmware-ul ([03-firmware.md](03-firmware.md)).
2. Leagă provizoriu (breadboard / fire Dupont) totul conform [04-cablaj.md](04-cablaj.md).
3. Pornește: trebuie să apară logo-ul, apoi ecranul modului ales de comutator.
4. Verifică:
   - comutatorul schimbă între **Automatik / Handbetrieb / Setup** (Automat / Manual / Setup);
   - encoderul schimbă valori, iar butonul lui confirmă;
   - butonul verde pornește servo-ul (simbolul ▶), cel roșu îl oprește (⏸);
   - apăsarea pe celula de sarcină schimbă greutatea afișată.

## 5.2 Cântarul

Cântarul are 3 piese: `scale-ground-plate` (baza), `scale-top-plate` (platforma) și
`scale-topping-plate` (capacul).

1. Așază HX711 în baza cântarului și trece firele celulei.
2. Prinde un capăt al celulei de **bază** cu **2 × M5 × 20** cap înecat (găurile Ø5,1) și celălalt capăt
   de **platformă** cu **2 × M4 × 20** cap înecat (găurile Ø4,1). Celula trebuie să lucreze „în consolă”:
   - săgeata de pe celulă indică direcția forței (în jos);
   - placa de sus **nu are voie să atingă** partea de jos sau carcasa – lasă un spațiu de 1–2 mm.
3. Pune capacul de protecție peste placa de sus, ca mierea să nu curgă pe șuruburi.
4. Așază cântarul pe o suprafață plană și stabilă; vibrațiile mesei se văd în citiri.

## 5.3 Unitatea de control

1. Montează în capac (`housing-upper-part`): encoderul (gaura Ø7,4, cu piulița lui), cele două butoane de
   12 mm (Ø12,5 – verde = START, roșu = STOP) și comutatorul rotund de 20 mm (Ø20,5).
   Buzzer-ul (opțional) nu are loc dedicat – lipește-l în interior.
2. Așază placa Heltec în locaș cu ecranul spre fereastră și fixeaz-o cu puțin **superglue**
   (varianta carcasei din 11/2023). Nu pune adeziv pe butoanele PRG/RST sau pe mufa USB.
3. Lipește firele (sau folosește un mic PCB de prototipare) conform tabelului de cablaj.
4. În cutie (`housing-ground-part`) montează mufa DC (gaura Ø8,2) și trece cablurile spre cântar și
   servo prin cele două găuri Ø6,1. Fă un nod sau pune o clemă pe interior ca să nu se smulgă firele.
5. Îmbină cele două părți prin presare (nu sunt necesare șuruburi).

## 5.4 Mecanismul robinetului (servo + roți dințate)

> ⚠️ **Cuplează servo-ul la robinet abia după prima pornire cu firmware-ul încărcat.**
> La pornire servo-ul se duce automat în poziția „închis” (`winkel_min`). Dacă îl montezi înainte,
> poate forța robinetul sau piesele printate.

1. Montează suportul servo (`servo-mounting-plate`) pe robinetul maturatorului – se prinde fix pe
   corpul robinetului Imgut.
2. Prinde servo-ul în suport cu **2 × M3 × 20** + piulițe + șaibe.
3. Înșurubează roata dințată `gear-on-servo` pe **discul metalic 25T** cu **5 × M3 × 15** + șaibe.
   (Discul **nu** se pune încă pe axul servo-ului.)
4. Montează brațul cu sector dințat (`gear-arm`) pe robinet: **M3 × 30** + piuliță + șaibe și
   **M6 × 50** (axul) – vezi [`hardware/README.md`](../hardware/README.md#unde-merge-fiecare-șurub) și
   proiectul Fusion pentru poziția exactă.
5. Pornește electronica **fără discul pe servo**. Servo-ul ajunge în poziția „închis”.
6. Închide robinetul manual (strâns, cum îl închizi normal).
7. Pune discul cu roata dințată pe axul servo-ului astfel încât dinții să se angreneze cu brațul în
   această poziție „închis”, apoi strânge șurubul central al discului.
8. Treci în **modul Manual** (comutatorul pe mijloc), apasă **verde** și rotește încet encoderul:
   robinetul trebuie să se **deschidă** la creșterea unghiului. Dacă se închide/forțează,
   `QUETSCHHAHN_LINKS` nu este activ în firmware (vezi [03-firmware.md](03-firmware.md)).
9. Notează unghiul afișat (W=…) la care robinetul:
   - abia e închis etanș → **Minimum**;
   - e deschis complet → **Maximum**;
   - lasă un fir subțire de miere → **Feindosierung** (dozare fină).

   Aceste valori se introduc în **Setup → Servowinkel** ([06-calibrare-utilizare.md](06-calibrare-utilizare.md)).

## 5.5 Poziționarea finală

- Cântarul se pune sub robinet astfel încât jetul să cadă în centrul borcanului.
- Unitatea de control lângă, la îndemână, ferită de picături.
- Cablurile prinse astfel încât să nu tragă de cântar (orice tensiune pe cablu modifică greutatea).
