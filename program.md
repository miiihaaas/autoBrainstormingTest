# autobudget — Autonomno istraživanje za projektni zadatak: Budžetsko računovodstvo u školstvu

Ovo je eksperiment u kojem LLM autonomno istražuje domenu budžetskog računovodstva u školstvu i generiše sveobuhvatnu dokumentaciju koja će služiti kao podloga za pisanje projektnog zadatka za izradu Django aplikacije.

## Setup

Za pokretanje novog istraživanja, dogovori se sa korisnikom:

1. **Dogovori run tag**: predloži tag na osnovu današnjeg datuma (npr. `mar29`). Grana `autobudget/<tag>` ne smije već postojati — ovo je svježi run.
2. **Kreiraj granu**: `git checkout -b autobudget/<tag>` od trenutnog main-a.
3. **Pročitaj kontekstualne fajlove**: Repo je mali. Pročitaj ove fajlove za puni kontekst:
   - `budžetsko_računovodstvo.md` — početni brainstorming, pojmovi, funkcionalni zahtjevi.
   - `program.md` — ovaj fajl. Pravila rada i istraživanja.
4. **Inicijaliziraj results.tsv**: Kreiraj `results.tsv` sa header redom.
5. **Potvrdi i kreni**: Potvrdi da je setup u redu.

Kad dobiješ potvrdu, pokreni istraživačku petlju.

## Cilj

**NE pišeš kod.** Tvoj zadatak je da istražiš domenu i generišeš detaljnu dokumentaciju koja pokriva sve aspekte budžetskog računovodstva u školstvu. Ova dokumentacija će kasnije služiti kao osnova za pisanje formalnog projektnog zadatka za izradu Django aplikacije.

Za svaku temu/modul generiši zaseban `.md` fajl u folderu `research/` sa dubinskim istraživanjem.

**Tech stack za koji se priprema dokumentacija: Django (Python), PostgreSQL.**

## Domena

Radiš istraživanje za modul budžetskog računovodstva za obrazovne institucije (osnovne škole, srednje škole, visokoškolske ustanove) u Bosni i Hercegovini. Ove institucije su **budžetski korisnici** — finansiraju se iz javnih sredstava i podliježu strogim zakonskim regulativama.

### Ključni koncepti koje moraš istražiti:
- **Kontni plan za budžetske korisnike** (klase 0-9) — temelj cijelog modula
- **Budžetska klasifikacija** — ekonomska, organizaciona, funkcionalna, programska
- **Plate i doprinosi** — 80-90% budžeta škole, najkompleksniji obračun
- **Trezorski sistem** — škole ne plaćaju direktno, sve ide preko trezora
- **Fiskalna godina** — svi planovi i izvještaji su godišnji, sa mjesečnim/kvartalnim presjecima
- **Pravni okvir BiH** — zakoni na državnom, entitetskom i kantonalnom nivou

## Šta istražuješ i generišeš

Za svaku temu kreiraj detaljan dokument u `research/` folderu:

### FAZA 1 — Pravni i regulatorni okvir
| Fajl | Sadržaj |
|---|---|
| `research/01_pravni_okvir.md` | Svi relevantni zakoni i propisi (FBiH, RS, BD). Zakon o budžetima, Zakon o računovodstvu, pravilnici. Citati ključnih članova. |
| `research/02_kontni_plan.md` | Detaljan kontni plan za budžetske korisnike u školstvu. Sve klase, grupe, sintetički i analitički konti sa objašnjenjima. Primjeri knjiženja. |
| `research/03_budzetske_klasifikacije.md` | Ekonomska, organizaciona, funkcionalna i programska klasifikacija. Kako se primjenjuju u školstvu. Šifrarnici. |

### FAZA 2 — Finansijski procesi
| Fajl | Sadržaj |
|---|---|
| `research/04_glavna_knjiga.md` | Kako funkcioniše glavna knjiga budžetskog korisnika. Double-entry princip. Dnevnik, analitika, sintetika. Primjeri knjiženja za škole. |
| `research/05_budzet_planiranje.md` | Proces planiranja budžeta škole. Ko učestvuje, rokovi, dokumenti. Rebalans. Primjer budžeta osnovne škole. |
| `research/06_budzet_izvrsenje.md` | Praćenje izvršenja budžeta. Mjesečni operativni planovi. Zahtjevi za dodjelu sredstava. Izvještaji. |
| `research/07_trezorski_sistem.md` | Kako funkcioniše trezorski sistem. JRT (jedinstveni račun trezora). Kako škole plaćaju preko trezora. Nalozi, odobrenja. |

### FAZA 3 — Obračun plata
| Fajl | Sadržaj |
|---|---|
| `research/08_plate_osnove.md` | Struktura plate u školstvu. Osnovica, koeficijenti po zvanjima (nastavnik, profesor, direktor...). Platni razredi. Kolektivni ugovor. |
| `research/09_plate_dodaci.md` | Svi dodaci na platu: minuli rad, razredništvo, mentorstvo, rad u otežanim uslovima, prekovremeni. Formule obračuna. |
| `research/10_doprinosi_porezi.md` | Doprinosi iz plate i na platu (PIO, zdravstveno, nezaposlenost). Porez na dohodak. Stope po entitetima. Primjer kompletnog obračuna. |
| `research/11_bolovanja_odsustva.md` | Obračun bolovanja (42 dana poslodavac, dalje fond). Porodiljsko. Godišnji odmor. Plaćeno/neplaćeno odsustvo. |
| `research/12_honorari_ugovori.md` | Ugovori o djelu, autorski honorari. Obračun poreza i doprinosa. Specifičnosti za vanjske saradnike u školi. |

### FAZA 4 — Imovina i nabavke
| Fajl | Sadržaj |
|---|---|
| `research/13_javne_nabavke.md` | Zakon o javnim nabavkama BiH. Pragovi, postupci (direktni sporazum, konkurentski zahtjev, otvoreni). Plan nabavki škole. |
| `research/14_imovina_amortizacija.md` | Evidencija imovine budžetskog korisnika. Kategorije (objekti, oprema, IT, namještaj). Stope amortizacije. Popis. Otpis. |
| `research/15_blagajna_banka.md` | Blagajničko poslovanje škole. Limiti gotovine. Bankovni izvodi. Uparivanje. Format naloga za plaćanje. |

### FAZA 5 — Izvještavanje
| Fajl | Sadržaj |
|---|---|
| `research/16_finansijski_izvjestaji.md` | Bilans stanja, bilans uspjeha, izvještaj o novčanim tokovima. Forme i obrasci. Rokovi podnošenja. |
| `research/17_budzet_izvjestaji.md` | Izvještaj o izvršenju budžeta (mjesečni, kvartalni, godišnji). Forme. Ko ih prima. |
| `research/18_statisticki_izvjestaji.md` | Izvještaji za zavod za statistiku, ministarstvo obrazovanja. Obrasci. Rokovi. |

### FAZA 6 — Specifikacija za Django
| Fajl | Sadržaj |
|---|---|
| `research/19_django_modeli.md` | Prijedlog Django modela (models.py) za sve module. Relacije, polja, validacije. Decimal polja za financije. |
| `research/20_django_api.md` | Prijedlog API endpointa (DRF ili views). CRUD za sve entitete. Filteri, paginacija. |
| `research/21_django_admin.md` | Prijedlog Django admin konfiguracije. Inline modeli, filteri, akcije. |
| `research/22_projektni_zadatak.md` | **FINALNI DOKUMENT** — formalni projektni zadatak za izradu aplikacije, sintetizovan iz svega prethodnog. |

## Pravila istraživanja

**Šta MOŽEŠ raditi:**
- Kreirati i modificirati `.md` fajlove u `research/` folderu
- Koristiti web pretragu za zakone, propise, pravilnike, kolektivne ugovore
- Koristiti LLM znanje o računovodstvu, finansijama, Django frameworku
- Commitovati svaki završeni dokument

**Šta NE MOŽEŠ raditi:**
- Mijenjati `budžetsko_računovodstvo.md` — to je početni referentni dokument (read-only)
- Pisati Python/Django kod — samo specifikacije i prijedloge modela u markdown-u
- Izmišljati brojeve za poreske stope ili koeficijente — koristi web pretragu za tačne podatke
- Preskočiti web pretragu za pravne teme — propisi se mijenjaju, tvoje znanje može biti zastarjelo

**Kvalitet dokumenta**:
- Svaki dokument mora biti **detaljan i konkretan** — ne generički
- Uključi **primjere** gdje god je moguće (primjer knjiženja, primjer obračuna plate, primjer budžeta)
- Citiraj **konkretne zakone i članove** — ne "prema zakonu" nego "prema članu 45. Zakona o budžetima FBiH"
- Za formule obračuna daj **numeričke primjere** sa realnim brojevima
- Ako nešto varira po kantonima/entitetima, **navedi razlike**

**Kriterij kompletnosti**: Dokument je kompletiran kad sadrži dovoljno informacija da programer koji nikad nije radio sa budžetskim računovodstvom može na osnovu njega napisati funkcionalan Django modul.

## Output format

Nakon svake iteracije (završenog dokumenta), zapiši rezime:

```
---
tema:               kontni_plan
fajl:               research/02_kontni_plan.md
status:             complete | partial | needs_review
web_sources:        3
examples_included:  5
laws_cited:         2
word_count:         ~2500
---
```

## Logovanje rezultata

Kad je iteracija gotova, zapiši u `results.tsv` (tab-separated).

TSV ima header red i 6 kolona:

```
commit	tema	fajl	status	sources	description
```

1. git commit hash (short, 7 chars)
2. naziv teme (npr. kontni_plan, plate_osnove, javne_nabavke)
3. putanja do fajla (npr. research/02_kontni_plan.md)
4. status: `complete`, `partial`, ili `needs_review`
5. broj izvora (web + zakonski) korištenih
6. kratak opis šta dokument pokriva

Primjer:

```
commit	tema	fajl	status	sources	description
a1b2c3d	pravni_okvir	research/01_pravni_okvir.md	complete	8	zakoni FBiH/RS/BD — budžet, računovodstvo, trezor, javne nabavke
b2c3d4e	kontni_plan	research/02_kontni_plan.md	complete	5	kontni plan klase 0-9 sa primjerima knjiženja za škole
c3d4e5f	plate_osnove	research/08_plate_osnove.md	partial	3	osnovice i koeficijenti — nedostaju podaci za RS
```

## Petlja istraživanja

Istraživanje se odvija na dediciranoj grani (npr. `autobudget/mar29`).

LOOP ZAUVIJEK:

1. **Provjeri git stanje**: šta je do sad urađeno, koji dokumenti postoje u `research/`.
2. **Odaberi sljedeću temu** po redoslijedu faza (1→2→3→4→5→6). Unutar faze idi redom.
3. **Istraži temu**:
   - Koristi web pretragu za zakone, propise, stope, obrasce
   - Provjeri više izvora — ne oslanjaj se na jedan
   - Za BiH specifičnosti traži na ba domenama, službenim glasnicima
4. **Napiši dokument** u `research/` folderu — detaljan, sa primjerima i citatima.
5. **Provjeri kvalitet**:
   - Da li je dovoljno detaljan da programer može kodirati na osnovu njega?
   - Da li su navedeni konkretni zakoni i članovi?
   - Da li ima numeričke primjere?
   - Ako ne — dopuni prije nego nastaviš dalje.
6. **Commituj** dokument sa opisnim commit message-om.
7. **Zapiši** u results.tsv (NE commitovati results.tsv).
8. **Nastavi** sa sljedećom temom.

Ako otkriješ da prethodni dokument treba dopunu (npr. istraživanje plata otkriva da pravni okvir nije dovoljno detaljan), **vrati se i dopuni** — ali zapiši to kao zasebnu iteraciju u results.tsv.

## Prioriteti i redoslijed

```
FAZA 1 — Pravni temelj (OBAVEZNO PRVO)
├── 01_pravni_okvir           ← zakoni i propisi
├── 02_kontni_plan            ← klase, grupe, analitički konti
└── 03_budzetske_klasifikacije ← ekonomska, org., funkcionalna, programska

FAZA 2 — Finansijski procesi
├── 04_glavna_knjiga          ← double-entry, dnevnik, salda
├── 05_budzet_planiranje      ← proces, rokovi, dokumenti
├── 06_budzet_izvrsenje       ← praćenje, operativni planovi
└── 07_trezorski_sistem       ← JRT, nalozi, odobrenja

FAZA 3 — Plate i doprinosi
├── 08_plate_osnove           ← osnovice, koeficijenti, zvanja
├── 09_plate_dodaci           ← minuli rad, razredništvo, formule
├── 10_doprinosi_porezi       ← stope, obračun, primjeri
├── 11_bolovanja_odsustva     ← naknade, fondovi, trajanja
└── 12_honorari_ugovori       ← ugovori o djelu, autorski

FAZA 4 — Imovina i nabavke
├── 13_javne_nabavke          ← pragovi, postupci, plan
├── 14_imovina_amortizacija   ← registar, stope, popis
└── 15_blagajna_banka         ← gotovina, izvodi, nalozi

FAZA 5 — Izvještavanje
├── 16_finansijski_izvjestaji ← bilans, cash flow, forme
├── 17_budzet_izvjestaji      ← izvršenje, kvartalni
└── 18_statisticki_izvjestaji ← ministarstvo, zavod za statistiku

FAZA 6 — Django specifikacija (FINALNA FAZA)
├── 19_django_modeli          ← models.py prijedlog
├── 20_django_api             ← views/DRF prijedlog
├── 21_django_admin           ← admin konfiguracija
└── 22_projektni_zadatak      ← FINALNI projektni zadatak
```

## NIKAD NE STAJ

Jednom kad petlja istraživanja počne (nakon inicijalnog setup-a), NE zaustavljaj se da pitaš korisnika da li da nastaviš. NE pitaj "da li da nastavim?" ili "je li ovo dobra tačka za pauzu?". Korisnik možda spava ili nije za računarom i očekuje da nastavljaš raditi **neograničeno** dok te ručno ne zaustavi. Ti si autonoman.

Ako ti ponestane tema iz liste — vrati se na već napisane dokumente i dopuni ih sa novim saznanjima. Cross-referenciraj dokumente međusobno. Provjeri konzistentnost podataka. Dodaj više primjera. Istraži edge cases.

Ako web pretraga ne daje rezultate za neku specifičnost — zapiši to eksplicitno u dokumentu kao "POTREBNA VERIFIKACIJA: [šta treba provjeriti]" i nastavi dalje.

Korisnik se može vratiti i naći 22 detaljno istražena dokumenta koji čine kompletnu osnovu za projektni zadatak.
