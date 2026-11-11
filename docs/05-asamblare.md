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

Cântarul are 3 piese: **partea de jos**, **placa de sus** și **capacul de protecție**.

1. Așază HX711 în locașul din partea de jos și trece firele celulei.
2. Prinde **un capăt** al celulei de partea de jos și **celălalt capăt** de placa de sus (șuruburile
   intră în găurile filetate ale celulei). Celula trebuie să lucreze „în consolă”:
   - săgeata de pe celulă indică direcția forței (în jos);
   - placa de sus **nu are voie să atingă** partea de jos sau carcasa – lasă un spațiu de 1–2 mm.
3. Pune capacul de protecție peste placa de sus, ca mierea să nu curgă pe șuruburi.
4. Așază cântarul pe o suprafață plană și stabilă; vibrațiile mesei se văd în citiri.

## 5.3 Unitatea de control

1. Montează în partea de sus a carcasei: encoderul, butonul verde, butonul roșu, comutatorul și buzzer-ul.
2. Așază placa Heltec în locaș cu ecranul spre fereastră și fixeaz-o cu puțin **superglue**
   (varianta carcasei din 11/2023). Nu pune adeziv pe butoanele PRG/RST sau pe mufa USB.
3. Lipește firele (sau folosește un mic PCB de prototipare) conform tabelului de cablaj.
4. Montează conectorii pentru cântar, servo și alimentare în partea de jos a carcasei.
5. Îmbină cele două părți prin presare (nu sunt necesare șuruburi).

## 5.4 Mecanismul robinetului (servo + roți dințate)

> ⚠️ **Cuplează servo-ul la robinet abia după prima pornire cu firmware-ul încărcat.**
> La pornire servo-ul se duce automat în poziția „închis” (`winkel_min`). Dacă îl montezi înainte,
> poate forța robinetul sau piesele printate.

1. Montează suportul servo pe robinetul maturatorului (suportul se prinde fix de robinet).
2. Înșurubează servo-ul în suport.
3. Pornește electronica **fără roata de pe servo**. Servo-ul ajunge în poziția „închis”.
4. Închide robinetul manual (strâns, cum îl închizi normal).
5. Montează roata dințată pe robinet și roata de pe servo, astfel încât dinții să se angreneze în
   această poziție „închis”.
6. Treci în **modul Manual** (comutatorul pe mijloc), apasă **verde** și rotește încet encoderul:
   robinetul trebuie să se **deschidă** la creșterea unghiului. Dacă se închide/forțează,
   `QUETSCHHAHN_LINKS` nu este activ în firmware (vezi [03-firmware.md](03-firmware.md)).
7. Notează unghiul afișat (W=…) la care robinetul:
   - abia e închis etanș → **Minimum**;
   - e deschis complet → **Maximum**;
   - lasă un fir subțire de miere → **Feindosierung** (dozare fină).

   Aceste valori se introduc în **Setup → Servowinkel** ([06-calibrare-utilizare.md](06-calibrare-utilizare.md)).

## 5.5 Poziționarea finală

- Cântarul se pune sub robinet astfel încât jetul să cadă în centrul borcanului.
- Unitatea de control lângă, la îndemână, ferită de picături.
- Cablurile prinse astfel încât să nu tragă de cântar (orice tensiune pe cablu modifică greutatea).
