# 7. Depanare

| Problemă | Cauză probabilă | Soluție |
|----------|-----------------|---------|
| Ecranul rămâne negru | firmware pentru altă placă (V1/V2) sau placă greșită aleasă la compilare | Compilează cu `board = heltec_wifi_kit_32_V3` și `HARDWARE_LEVEL 3` (setările din acest repo). |
| Upload-ul nu pornește | placa nu intră în modul de programare / cablu doar de încărcare / lipsește driverul CP210x | Ține **PRG**, apasă **RST**, eliberează PRG, reîncearcă. Alt cablu USB-C. Instalează driverul Silicon Labs CP210x. |
| „Keine Waage!” | HX711 nedetectat | Verifică VCC (3V3), GND, DT → GPIO 39, SCK → GPIO 38. DT și SCK inversate sunt o greșeală frecventă. |
| „Nicht kalibr.” la pornire | cântarul nu a fost calibrat (sau ai făcut *Clear Prefs* / *Erase flash*) | Setup → **Kalibrieren**. |
| „Waage leeren!” la pornire | era ceva pe cântar (> 20 g) la pornire | Golește cântarul în cele 5 s cât e afișat mesajul; firmware-ul reîncearcă apoi tara singur. |
| Greutatea crește negativ când apeși | firele de semnal ale celulei inversate sau celula montată invers | Inversează A+ cu A− pe HX711 (sau întoarce celula) și recalibrează. |
| Greutatea „plutește” / sare | celula atinge carcasa, cablu tras, vibrații, curenți de aer, zgomot de la servo | Verifică spațiul liber al plăcii de sus, separă cablul HX711 de cel al servo-ului, lasă 2–3 min de încălzire. În ultimă instanță activează `FEHLERKORREKTUR_WAAGE`. |
| Placa se resetează când pornește servo-ul | sursa prea slabă / GND necomun / fire subțiri | Sursă ≥ 3 A, GND comun, condensator 470–1000 µF la servo, fire mai groase pe alimentare. |
| Servo-ul închide când ar trebui să deschidă | `QUETSCHHAHN_LINKS` inactiv | Folosește firmware-ul din acest repo (îl are activat) – nu binarul oficial upstream. |
| Robinetul nu se închide complet | `Minimum` prea mare sau roțile montate decalat | Reglează **Servowinkel → Minimum** cu *Livesetup ein*; dacă nu ajunge, remontează roata cu un dinte mai departe. |
| Servo-ul bâzâie / forțează în capăt | unghiuri peste limita mecanică | Micșorează `Maximum` / mărește `Minimum`. Eventual dezactivează `SERVO_ERWEITERT`. |
| Encoderul sare câte 2 valori pe clic | tip de encoder diferit (ex. HW-040) | `#define ROTARY_SCALE 1`. |
| Encoderul merge invers | CLK și DT inversate | Schimbă firele de pe GPIO 47 și 48. |
| Automat și Setup sunt inversate | firele comutatorului | Schimbă firele de pe GPIO 40 și 42. |
| Butonul verde nu pornește automatul | tara nesetată pentru cantitatea aleasă | Setup → **Tarawerte** pentru acea cantitate. |
| Autostart nu pornește | borcanul diferă de tară cu mai mult decât toleranța, sau greutatea nu e stabilă 1,5 s | Refă tara pentru tipul de borcan, mărește **Glastol.**, evită să atingi borcanul. |
| Borcanele ies prea pline | mierea mai curge după închidere | Corecție mai negativă, `Feindos.` mai mic, sau activează **Autokorr.** |
| Borcanele ies prea goale | corecție prea negativă | Corecție mai mare; cu autocorecție, mărește **Kulanz**. |
| Buzzer-ul nu sună | buzzer dezactivat din meniu (implicit) sau buzzer pasiv | Setup → **Parameter → Buzzer ein**. Folosește un buzzer *activ*. |
| Setările au dispărut după reprogramare | s-a folosit „Erase flash” | Normal – refă calibrarea și setările. Upload-ul obișnuit nu le șterge. |

## Mesaje de depanare pe serial

În `hanimandl.cpp` decomentează `#define isDebug 4`, încarcă din nou și deschide monitorul serial
(115200 baud): `pio device monitor`. Vei vedea valorile brute ale cântarului, greutățile țintă, timpii.
Nu lăsa `isDebug` activ în utilizare normală (încetinește bucla de cântărire).

## Ajutor din comunitate

- Forum Hiveeyes (germană, foarte activ pe HaniMandl):
  <https://community.hiveeyes.org/t/hanimandl-halbautomatischer-honig-abfull-roboter/768>
- Comentariile modelului pe Printables: <https://www.printables.com/model/524971-filling-machine-hanimandl/comments>
