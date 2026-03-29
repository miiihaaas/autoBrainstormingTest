# Budžetsko računovodstvo u školstvu — Republika Srbija

## Projektni zadatak za izradu modula u aplikaciji

---

## 1. Uvod i kontekst

Budžetsko računovodstvo u školstvu obuhvata celokupan proces planiranja, evidentiranja, praćenja i izveštavanja o finansijskim sredstvima koja se koriste u obrazovnim institucijama (osnovne škole, srednje škole, visokoškolske ustanove). Ove institucije su indirektni korisnici budžetskih sredstava koji se finansiraju iz budžeta Republike Srbije i budžeta jedinica lokalne samouprave, i podležu strogim zakonskim regulativama.

---

## 2. Ključni pojmovi i oblasti

### 2.1 Budžet i budžetsko planiranje
- **Budžet** — finansijski plan prihoda i rashoda za fiskalnu (kalendarsku) godinu
- **Budžetski korisnik** — direktni (ministarstva) i indirektni (škole, ustanove) korisnici budžetskih sredstava
- **Aproprijacija** — odobreni iznos sredstava za određenu namenu u budžetu
- **Kvota** — odobreni iznos za trošenje u određenom periodu (mesec/kvartal)
- **Budžetska klasifikacija** — sistematizacija prihoda i rashoda po ekonomskim kategorijama
- **Organizaciona klasifikacija** — razvrstavanje po organizacionim jedinicama
- **Funkcionalna klasifikacija** — razvrstavanje po funkcijama (obrazovanje, uprava, održavanje)
- **Programska klasifikacija** — razvrstavanje po programima i programskim aktivnostima

### 2.2 Kontni plan za budžetski sistem
Prema Pravilniku o standardnom klasifikacionom okviru i Kontnom planu za budžetski sistem ("Službeni glasnik RS"):
- Klasa 0 — Nefinansijska imovina
- Klasa 1 — Finansijska imovina
- Klasa 2 — Obaveze
- Klasa 3 — Kapital, utvrđivanje rezultata poslovanja i vanbilansna evidencija
- Klasa 4 — Tekući rashodi (plate, korišćenje usluga i roba)
- Klasa 5 — Izdaci za nefinansijsku imovinu
- Klasa 6 — Izdaci za otplatu glavnice i nabavku finansijske imovine
- Klasa 7 — Tekući prihodi
- Klasa 8 — Primanja od prodaje nefinansijske imovine i zaduživanja
- Klasa 9 — Vanbilansna evidencija

### 2.3 Specifičnosti školstva u Srbiji
- **Plate i doprinosi** — najveća stavka rashoda (80-90% budžeta škole), isplaćuju se iz budžeta RS
- **Materijalni troškovi** — struja, grejanje, voda, komunalije, kancelarijski materijal — finansira lokalna samouprava
- **Nabavka udžbenika i nastavnih sredstava**
- **Održavanje objekata i opreme** — finansira lokalna samouprava (osnivač)
- **Prevoz učenika i zaposlenih**
- **Stipendije i pomoći učenicima**
- **Stručno usavršavanje nastavnika**
- **Vannastavne aktivnosti i takmičenja**
- **Projekti finansirani iz donacija i grantova**

---

## 3. Funkcionalni zahtevi modula

### 3.1 Modul: Budžetsko planiranje
| Funkcionalnost | Opis |
|---|---|
| Kreiranje finansijskog plana | Unos planiranih prihoda i rashoda po aproprijacijama za fiskalnu godinu |
| Rebalans budžeta | Mogućnost izmena plana tokom godine uz evidenciju verzija |
| Višegodišnje planiranje | Projekcije za 2-3 godine unapred |
| Šabloni | Predefinisani šabloni finansijskog plana za osnovne/srednje škole |
| Budžetski kalendar | Praćenje rokova za podnošenje i odobravanje finansijskog plana |
| Poređenje plan/izvršenje | Uporedni prikaz planiranih i ostvarenih iznosa po aproprijacijama |

### 3.2 Modul: Knjiženje i evidencija
| Funkcionalnost | Opis |
|---|---|
| Glavna knjiga | Vođenje glavne knjige po Kontnom planu za budžetski sistem |
| Dnevnik knjiženja | Hronološka evidencija svih finansijskih transakcija |
| Pomoćne knjige | Knjiga ulaznih faktura, knjiga izlaznih faktura, blagajna |
| Automatska knjiženja | Automatsko kontiranje čestih transakcija (plate, komunalije) |
| Storno i korekcije | Mogućnost ispravki sa punim audit tragom |
| Zaključivanje perioda | Mesečno i godišnje zaključivanje knjiga |

### 3.3 Modul: Obračun plata
| Funkcionalnost | Opis |
|---|---|
| Platni spisak | Obračun plata za nastavno i nenastavno osoblje |
| Koeficijenti i platne grupe | Obračun po koeficijentima složenosti poslova (Zakon o zaposlenima u javnim službama) |
| Doprinosi i porezi | PIO 25% (14%+11%), zdravstveno 10.3% (5.15%+5.15%), nezaposlenost 0.75%, porez 10% |
| Bolovanja i odsustva | Obračun naknada za bolovanje, porodiljsko, godišnji odmor |
| Minuli rad | 0.4% po navršenoj godini rada |
| Prekovremeni rad | Evidencija i obračun prekovremenog rada, zamena |
| Honorarni rad | Obračun honorara za spoljne saradnike |
| Eksport za trezor | Generisanje naloga za plaćanje kroz ISIB/trezorski sistem |

### 3.4 Modul: Javne nabavke
| Funkcionalnost | Opis |
|---|---|
| Plan nabavki | Godišnji plan javnih nabavki usklađen sa finansijskim planom |
| Postupci nabavke | Evidencija nabavki male vrednosti, otvoreni postupak, restriktivni |
| Ugovori | Praćenje ugovora sa dobavljačima, rokovi, iznosi |
| Portal javnih nabavki | Integracija sa Portalom javnih nabavki RS |

### 3.5 Modul: Izveštavanje
| Funkcionalnost | Opis |
|---|---|
| Periodični izveštaji | Mesečni, kvartalni, polugodišnji, godišnji finansijski izveštaji |
| Obrazac 1 — Bilans stanja | Automatsko generisanje bilansa stanja |
| Obrazac 2 — Bilans prihoda i rashoda | Prikaz prihoda i rashoda sa rezultatom poslovanja |
| Obrazac 3 — Izveštaj o novčanim tokovima | Cash flow izveštaj |
| Obrazac 5 — Izveštaj o kapitalnim izdacima | Pregled investicija u opremu i objekte |
| Izveštaj o izvršenju finansijskog plana | Uporedni prikaz plan vs. realizacija sa % izvršenja |
| Izveštaji za trezor | Zahtevi za plaćanje, mesečni planovi |
| Završni račun | Godišnji završni račun budžetskog korisnika |
| Custom izveštaji | Mogućnost kreiranja prilagođenih izveštaja |

### 3.6 Modul: Upravljanje imovinom
| Funkcionalnost | Opis |
|---|---|
| Registar imovine | Evidencija svih sredstava škole (objekti, oprema, nameštaj, IT) |
| Amortizacija | Automatski obračun amortizacije po propisanim stopama |
| Popis (inventura) | Podrška za godišnji popis sa komisijama |
| Otpis i rashod | Postupak otpisa dotrajale i neupotrebljive imovine |
| Sitni inventar | Posebna evidencija sitnog inventara |

### 3.7 Modul: Blagajna i bankovni izvodi
| Funkcionalnost | Opis |
|---|---|
| Blagajničko poslovanje | Vođenje blagajne sa primicima i izdacima |
| Blagajnički maksimum | Poštovanje zakonskog limita gotovine |
| Blagajnički izveštaj | Dnevni blagajnički izveštaj |
| Izvodi | Pregled prometa po konsolidovanom računu trezora |
| Trezorski sistem | Integracija sa ISIB sistemom Uprave za trezor |

---

## 4. Pravni i regulatorni okvir

### 4.1 Zakoni i propisi
- Zakon o budžetskom sistemu ("Sl. glasnik RS", br. 54/2009, sa izmenama i dopunama)
- Zakon o računovodstvu ("Sl. glasnik RS")
- Zakon o javnim nabavkama ("Sl. glasnik RS", br. 91/2019)
- Zakon o porezu na dohodak građana ("Sl. glasnik RS")
- Zakon o doprinosima za obavezno socijalno osiguranje ("Sl. glasnik RS")
- Zakon o radu ("Sl. glasnik RS")
- Zakon o zaposlenima u javnim službama ("Sl. glasnik RS")
- Zakon o osnovama sistema obrazovanja i vaspitanja ("Sl. glasnik RS")
- Pravilnik o standardnom klasifikacionom okviru i Kontnom planu za budžetski sistem
- Pravilnik o načinu pripreme, sastavljanja i podnošenja finansijskih izveštaja korisnika budžetskih sredstava
- Poseban kolektivni ugovor za zaposlene u ustanovama obrazovanja

### 4.2 Kontrole i revizija
- Interna finansijska kontrola u javnom sektoru (IFKJ)
- Budžetska inspekcija Ministarstva finansija
- Državna revizorska institucija (DRI)
- Uprava za trezor — kontrola izvršenja budžeta

---

## 5. Integracije sa drugim modulima aplikacije

```
+---------------------+       +------------------------+
|   HR / Kadrovi      |<----->|  Obračun plata         |
+---------------------+       +------------------------+
         |                              |
         v                              v
+---------------------+       +------------------------+
|   Norma časova      |       |  Glavna knjiga         |
+---------------------+       +------------------------+
         |                              |
         v                              v
+---------------------+       +------------------------+
|   Raspored          |       |  Izveštavanje          |
+---------------------+       +------------------------+
                                        |
                                        v
                              +------------------------+
                              |  Trezor (ISIB)         |
                              +------------------------+
```

### Ključne integracije:
- **HR/Kadrovi** → Plate: podaci o zaposlenima, koeficijenti, staž, zvanja
- **Norma časova** → Plate: fond časova, prekovremeni, zamene
- **Plate** → Glavna knjiga: automatsko knjiženje obračuna plata
- **Javne nabavke** → Budžet: provera raspoloživih aproprijacija
- **Sve** → Izveštavanje: podaci za sve vrste izveštaja
- **Glavna knjiga** → Trezor (ISIB): nalozi za plaćanje

---

## 6. Korisničke uloge i ovlašćenja

| Uloga | Prava pristupa |
|---|---|
| Direktor škole | Pregled svih izveštaja, odobravanje finansijskog plana i plaćanja |
| Računovođa/Šef računovodstva | Pun pristup svim modulima knjiženja i izveštavanja |
| Sekretar škole | Pregled, unos faktura, blagajna |
| Školski odbor | Uvid u finansijski plan i ključne finansijske izveštaje |
| Lokalna samouprava (osnivač) | Pregled izveštaja o materijalnim troškovima |
| Ministarstvo prosvete | Pregled zbirnih izveštaja |
| Uprava za trezor | Pregled izvršenja, odobravanje plaćanja |
| Revizor (DRI) | Read-only pristup svim podacima |

---

## 7. Nefunkcionalni zahtevi

- **Sigurnost** — šifrovanje podataka, autentifikacija, autorizacija po ulogama
- **Audit trail** — logovanje svih promena sa korisnikom, datumom i vremenom
- **Backup** — automatsko sigurnosno kopiranje podataka
- **Dostupnost** — cloud-based, pristup putem web browser-a
- **Performanse** — izveštaji do 10 sekundi, unos transakcija < 2 sekunde
- **Skalabilnost** — podrška za rad sa 1 do 500+ škola u sistemu
- **Usklađenost** — mogućnost prilagodbe promenama propisa bez programiranja
- **Jezik** — srpski (ćirilica i latinica)
- **Valuta** — RSD (dinari), svi iznosi na 2 decimale
- **Fiskalna godina** — kalendarska godina (01.01. — 31.12.)

---

## 8. Faze implementacije

### Faza 1 — Osnova (MVP)
- Kontni plan i glavna knjiga
- Dnevnik knjiženja
- Osnovni izveštaji (Obrazac 1, Obrazac 2)
- Korisničke uloge

### Faza 2 — Budžet i plate
- Finansijsko planiranje i praćenje izvršenja
- Obračun plata sa doprinosima
- Izveštaj o izvršenju finansijskog plana
- Integracija sa trezorskim sistemom

### Faza 3 — Prošireni moduli
- Javne nabavke
- Upravljanje imovinom i amortizacija
- Blagajničko poslovanje
- Izvodi sa KRT-a

### Faza 4 — Napredne funkcionalnosti
- Puna ISIB integracija
- Custom izveštaji i dashboard
- Višeškolski pregled za ministarstvo/lokalnu samoupravu
- Automatizacije i notifikacije

---

## 9. Rizici i izazovi

| Rizik | Mitigacija |
|---|---|
| Česte promene propisa | Konfigurabilan kontni plan i formule obračuna |
| Razlike u finansiranju (republika vs lokalna samouprava) | Parametrizacija po izvoru finansiranja |
| Otpor korisnika prema digitalizaciji | Obuka, intuitivno sučelje, postepena migracija |
| Kvalitet postojećih podataka | Faza čišćenja i migracije podataka pre go-live |
| Integracija sa ISIB trezorskim sistemom | Rana koordinacija sa Upravom za trezor |

---

## 10. Očekivani ishodi

- Automatizacija finansijskog poslovanja škola
- Smanjenje grešaka u knjiženju i obračunu plata
- Transparentnost trošenja javnih sredstava
- Brže i tačnije izveštavanje prema Upravi za trezor, DRI, ministarstvima
- Centralizovan pregled finansijskog stanja svih škola u sistemu
- Usklađenost sa zakonskim zahtevima
