                                                                      INKTIME

1.	Diagrama componente:

![Diagrama nu se poate afisa](<img width="1027" height="1022" alt="Screenshot (215)" src="https://github.com/Lawenda700/InkTime/blob/main/Images/Screenshot%20(216).png" />
)

 2.	BOM cu componentele folosite:


| Componentă | Link Producător (Datasheet & JLC) |
| :--- | :--- |
| **JUMPER_SJ** | [Link JLC](https://jlcpcb.com/partdetail/WurthElektronik-Jumper2/C2940092) |
| **C166112** | [Link JLC](https://jlcpcb.com/partdetail/RALEC-RTT017681FTH/C166112) |
| **GRM011R60J152KE01L** | [Link JLC](https://jlcpcb.com/partdetail/22429554-GRM011R60J152KE01L/C21012218) |
| **CAPACITOR_0201_L** | [Link JLC](https://jlcpcb.com/partdetail/Made_inChina-Capacitor15nf100v/C26191) |
| **CPF0201D7K68C1** | [Link JLC](https://jlcpcb.com/partdetail/TEConnectivity-CPF0201D10KC1/C4187156) |
| **CAP_0402** | [Link JLC](https://jlcpcb.com/partdetail/1879-0402B151K500NT/C1527) |
| **EVP-AKE31A_PAN** | [Link JLC](https://jlcpcb.com/partdetail/PANASONIC-EVPAKE31A/C569760) |
| **MOSFET_PCH-DMG2305UX-7** | [Link JLC](https://jlcpcb.com/parts/componentSearch?searchTxt=MOSFET_PCH-DMG2305UX-7) |
| **2450AT18B100E** | [Link JLC](https://jlcpcb.com/partdetail/JohansonDielectrics-2450AT18B100E/C2917717) |
| **INDUCTOR_0402_L** | [Link JLC](https://jlcpcb.com/partdetail/MurataElectronics-LQG15HS27NJ02D/C12669) |
| **XTAL_32KHZ** | [Link JLC](https://jlcpcb.com/partdetail/HCI-CO21H4_32_000kHz18JHPSTL/C2842) |
| **503480-2400** | [Link JLC](https://jlcpcb.com/partdetail/MOLEX-5034802400/C122434) |
| **744043680IND_4828-WE-TPC_WRE** | [Link JLC](https://jlcpcb.com/partdetail/1378-VHF160808H1N8ST/C1026) |
| **BMA423** | [Link JLC](https://jlcpcb.com/partdetail/BoschSensortec-BMA423/C189517) |
| **BQ25180YBGR** | [Link JLC](https://jlcpcb.com/partdetail/TexasInstruments-BQ25180YBGR/C3682423) |
| **DRV2605YZFR** | [Link JLC](https://jlcpcb.com/parts/componentSearch?searchTxt=DRV2605YZFR) |
| **USBLC6-2SC6Y** | [Link JLC](https://jlcpcb.com/partdetail/STMicroelectronics-USBLC62SC6Y/C2969755) |
| **MBR0530** | [Link JLC](https://jlcpcb.com/partdetail/78464-MBR0530/C77336) |
| **SI1308EDL-T1-GE3** | [Link JLC](https://jlcpcb.com/partdetail/TECHPUBLIC-SI1308EDL/C7603347) |
| **MAX17048G+T10** | [Link JLC](https://jlcpcb.com/partdetail/2777647-MAX17048GT10/C2682616) |
| **TPTP20R** | [Link JLC](https://jlcpcb.com/partdetail/DLL-PAD4Y/C24833714) |
| **KH-TYPE-C-16P** | [Link JLC](https://jlcpcb.com/partdetail/Shenzhen_KinghelmElec-KH_TYPE_C16P/C709357) |
| **MLP2016SR47MT0S1** | [Link JLC](https://jlcpcb.com/partdetail/TDK-MLP2016SR47MT0S1/C87545) |
| **NRF52840_QF** | [Link JLC](https://jlcpcb.com/partdetail/NordicSemicon-NRF52840_QFAA_FR/C3606918) |
| **RT6160AWSC** | [Link JLC](https://jlcpcb.com/partdetail/RichtekTech-RT6160AWSC/C7065276) |
| **TC2030-IDC** | [Link JLC](https://jlcpcb.com/partdetail/C90533) |
| **XTAL_37MHZ** | [Link JLC](https://jlcpcb.com/partdetail/SiTime-SIT8008AI_32_33E_37000000Y/C70717) |



3.Descriere functionalitate hardware


Produsul final( smartwatch-ul InkTime) este impartit pe mai multe module. Mai jos voi prezenta o descriere in detaliu a fiecarui modul in parte.


MCU

Microcontroller-ul nRF52840 reprezinta nucleul sistemului, acesta aflandu-se la centrul tuturor functionalitatilor oferite. Acesta este un SoC avansat optimizat pentru consum redus. Dispune astfel de un nucleu ARM Cortex-M4F cu unitate de virgulă mobilă (FPU) și suport integrat pentru BLE 5.3 (Bluetooth Low Energy). In materie de semnale de ceas acesta folosește un cristal extern de 32 MHz (HFXO) pentru procesarea rapidă și radio, respectiv un cristal de 32.768 kHz (LFXO) pentru menținerea timpului în modurile de sleep cu un consum minim de curent.

La MCU se conecteaza in primul rand un subsistem de alimentare si incarcare, pentru a mentine functionarea smartwatch-ului. Arhitectura de alimentare este concepută pentru a asigura stabilitatea tensiunii de 3.3V pe tot parcursul descărcării bateriei LiPo de 250 mAh. Modulele principale ale acestui subsistem sunt:

-LiPo Charger (BQ25180), care gestionează încărcarea și distribuția energiei prin tehnologia Power-path, permițând funcționarea sistemului în timp ce bateria se încarcă. El comunică prin I²C (adresa 0x6A) și raportează evenimente prin întreruperi pe pinul P0.11.

-Regulator DC (RT6160), ce reprezinta un convertor buck-boost care menține șina de VDD_3V3 stabilă. Acesta este configurat hardware (VSEL low) pentru a oferi o ieșire fixă și este mereu activat când sistemul este alimentat.

-Fuel Gauge (MAX17048), care monitorizează precis starea de încărcare a bateriei direct de la nodul VBAT. Utilizează interfața I²C (adresa 0x36) și poate declanșa alerte de baterie descărcată pe pinul P0.10.

- USB-C si Protecție ESD, portul USB-C fiind utilizat pentru încărcare și comunicație nativă USB cu nRF52840, iar liniile de date sunt protejate împotriva descărcărilor electrostatice prin componente dedicate montate lângă conector numite colectiv protective ESD.

Pentru ca ceasul sa ofere interactiunea cu utilizatorul caracteristica unui smartwatch, sunt introduce modulele E-Paper Drive Circuit si E-Paper Connector care se conecteaza la un E-Paper Display de 1.54 de inchi cu rezoluție de 200x200 de pixeli, optimizat pentru citirea în lumina soarelui. Acest subsistem comunică prin SPI folosind pinii: SCK (P0.02), MOSI (P0.03), CS (P0.05), DC (P0.15), RST (P0.16) și BUSY (P0.17). Pentru a elimina consumul rezidual (leakage), alimentarea ecranului (VEPD) este controlată de un tranzistor PFET (SI2301CDS). Firmware-ul activează poarta PFET (pin P1.01) doar în timpul actualizării imaginii, menținând ecranul complet deconectat electric în restul timpului. Ca si strategie de refresh se efectuează un partial refresh o dată pe minut pentru actualizarea orei și un full refresh periodic pentru a preveni efectul de "ghosting".


Pentru convenienta, putem considera urmatoarele 3 module ca facand parte dintr-un subsistem destinate interactiunii cu utilizatorul:

-Accelerometru (BMA421), care are ca functie detectarea pașilor (pedometer) și trezirea sistemului la mișcare, comunica printr-o interfață I²C (adresa 0x18) si include un algoritm integrat pentru numărarea pașilor, eliminând sarcina de procesare de pe MCU. Totodata trimite întreruperi pe pinul P0.08 (INT1) pentru trezirea sistemului.

- Haptic Driver (DRV2605L), care alerteaza utilizatorului prin vibrații discrete (ERM motor). Acesta comunică prin I²C (adresa 0x5A) pentru selectarea modelelor de vibrație. Totodata, dispune de un pin de Enable (P0.12) pentru oprirea completă a driverului între notificări.

- Butoane, 3 la numar (Up: P0.13, Down: P0.14, Enter/Esc: P1.00) conectate direct la masă (active-low). Acestea utilizează rezistențe interne de pull-up și sunt configurate ca surse de trezire din sleep.


Un ultim modul este cel de programare și depanare (SWD). Se utilizeaza interfața Tag-Connect TC2030 pentru programarea și depanarea prin SWD (Serial Wire Debug). Semnalele utilizate de catre acesta sunt: SWDIO, SWDCLK, nRESET și GND . Totodata, el este conectat la o tensiune de referinta de 3.3V pentru a permite debugger-ului să detecteze tensiunea logică a sistemului, fără a alimenta placa direct din programator.




4.	Descrierea pinilor nRF52840

   Pinii P0.06 (SDA) și P0.07 (SCL) sunt utilizati pentru magistrala I²C. Aceștia sunt configurați pentru perifericul TWI (Two-Wire Interface) al MCU-ului. Sunt utilizați pentru a comunica cu majoritatea componentelor de pe placă (accelerometru, fuel gauge, haptic driver, charger și regulator) folosind o singură pereche de fire. S-au ales acești pini pentru a centraliza controlul senzorilor și a eficientiza rutarea pe PCB.

P0.02 (SCK), P0.03 (MOSI), P0.05 (CS), P0.15 (DC - Data/Command), P0.16 (RST - Reset) si P0.17 (BUSY) sunt folositi pentru afișajul E-paper (SPI și Control). Interfața SPI este necesară pentru transferul rapid al datelor imaginii către ecran. Pinul BUSY este esențial deoarece ecranul e-paper are nevoie de timp pentru procesarea fizică a particulelor de cerneală, iar MCU-ul trebuie să aștepte semnalul de „gata” înainte de a trimite noi comenzi sau de a opri alimentarea.

P1.01 este utilizat pentru gestiunea energiei ecranului (Power Gating.). Acest pin controlează poarta tranzistorului PFET care alimentează ecranul (VEPD). Alegerea unui pin dedicat pentru power gating permite eliminarea completă a consumului de curent rezidual (leakage) al ecranului în perioadele de repaus, o strategie critică pentru atingerea autonomiei de peste 30 de zile.

P0.13 (Up), P0.14 (Down), P1.00 (Enter/Esc) sunt utilizati pentru interfața cu utilizatorul(Butoanele). Acești pini sunt utilizați cu rezistențe interne de pull-up și sunt configurați pentru a detecta tranziția la nivel „low” (apăsare). Sunt selectați special pentru capacitatea lor de a genera evenimente de trezire (wake-up) din modul Deep Sleep, permițând utilizatorului să activeze ceasul instantaneu.
P0.08 (INT1 BMA421),P1.08 (INT2 BMA421), P0.10 (ALRT MAX17048) si P0.11 (INT BQ25180) sunt utilizati ca semnale de intrerupere și trezire (Senzori). Acești pini sunt utilizați pentru a primi semnale de la senzori fără ca MCU-ul să îi interogheze constant (polling). De exemplu, pinul P0.08 permite accelerometrului să trezească ceasul doar atunci când detectează pași sau mișcare, economisind energie masiv.

P0.12 (EN) este pentru controlul haptic. Acesta permite MCU-ului să oprească alimentarea logică a driverului între notificări, prevenind orice consum inutil în perioadele de liniște.

Pentru comunicatii native si debugging avem:
- Pini dedicați USB (D+/D-): Utilizați pentru interfața nativă USB a nRF52840, necesară pentru încărcare și comunicația de date/programare.
-  SWDIO și SWDCLK: Pini dedicați pentru programare și depanare prin SWD (Serial Wire Debug), rutați către conectorul Tag-Connect pentru acces rapid la memoria flash.
- nRESET (P0.18): Pinul de reset hardware, conectat la interfața de programare pentru a permite resetarea forțată în timpul dezvoltării sau recuperării.
-ANT: Acesta este pinul de ieșire pentru semnalul radio Bluetooth. Este conectat la o rețea de adaptare a impedanței (matching network) și ulterior la antena PCB-ului. Designul trebuie să urmeze strict geometria de referință Nordic pentru a asigura performanța BLE.

-VBUS: Pin conectat la alimentarea de 5V provenită din USB pentru a permite MCU-ului să detecteze momentul în care cablul este introdus.

Pentru alimentare avem:
-VDD și VDDH: Ambii sunt conectați la șina de VDD_3V3. Deoarece tensiunea este de 3.3V, cipul funcționează în „normal-voltage mode”.
-DCC: Este pinul de ieșire al regulatorului DC/DC intern. Acesta este conectat la un circuit extern format dintr-un inductor de 10uH și unul de 15nH, care alimentează nodul DEC4/DEC6. Firmware-ul activează acest regulator (DCDC1) la runtime pentru a reduce consumul de energie.

-VSS și Exposed Pad: Sunt conectați direct la planul de masă (GND) al PCB-ului pentru a asigura o cale de întoarcere a curentului și disipare termică.

Pentru ceas, se utilizeaza 2 surse externe pentru a echilibra performanța cu economia de energie. Pinii utilizati sunt:
 XC1 și XC2: Pini pentru cristalul de 32MHz (HFXO). Acesta este ceasul de mare viteză utilizat în timpul procesării intensive și pentru funcționarea radioului BLE.
 XL1 și XL2: Pini pentru cristalul de 32.768kHz (LFXO). Acesta permite menținerea timpului (RTC) cu precizie ridicată în timp ce ceasul este în modul de somn profund (Deep Sleep).




5.	Procesul de realizare al design-ului

 S.a inceput prin realizarea schematic-ului in Fusion, conform specificatilor cerute pentru produs in fisierele MRD, PRD, ERD, Detailed Design, cat si cu ajutorul schemei de support oferite. Dupa finalizarea acestuia, rezolvarea erorilor si minimizarea warning-urilor s-a trecut la partea de pcb 2d unde s-a folosit placa specificata, iar butoanele, conectorul USB si E-Paper Display Connector au fost puse in locurile recomandate, urmand amplasarea celorlalte componente si decuparea placutei sub antenna. Apoi a inceput procesul de rutare manuala a legaturilor pe 4 layere, rutele de putere fiind realizate cu o grosime de 0.3 mm, iar celelalte rute s-au realizat cu o grosime de 0.15 mm. S-a incercat pe cat posibila evitarea vias-urilor in realizarea rutelor de putere. Din cauza aglomerarii placii s-au acceptat anumite erori de suprapunere a componentelor( cele mai multe fiind reprezentate de prinderea viasurilor in pini sau suprapuneri intre viasuri in apropierea MCU). S-au acceptat si erorile de board outline generate de modelele componentelor si cateva erori de copper clearence generate de impunerea grosimii de 0.3 mm pentru rutile de putere ce interfera cu alti pini ai anumitor componente la conectare( orice alta eroare de copper clearence a fost rezolvata). Layer-ul de ground a fost folosit exclusive pentru pinii de gnd, iar planul de masa s-a realizat pe toate cele 4 layere si s-a facut vias stitching. S-a trecut apoi la realizarea pcb-ului 3d, unde mai intai s-au important modelele 3d pentru componente, mai putin pentru test-pads pentru care s-a create de la 0 modelul 3d. Pentru adaptor modelul 3d gasit a fost redus in dimensiune pentru a incapea in carcasa. Dupa, pcb-ul a fost introdus in carcasa oferita si s-au realizat modele simpliste de baterie, display si shaker finalizand astfel etapa de proiectare.  
