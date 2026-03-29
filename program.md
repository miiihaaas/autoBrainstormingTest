# autobudget — Autonomno istraživanje za projektni zadatak: Budžetsko računovodstvo u školstvu

Ovo je eksperiment u kojem LLM autonomno istražuje domenu budžetskog računovodstva u školstvu u Republici Srbiji i generiše sveobuhvatnu dokumentaciju koja će služiti kao podloga za pisanje projektnog zadatka za izradu Django aplikacije.

Sav output se piše na **srpskom jeziku**.

## Setup

Za pokretanje novog istraživanja, dogovori se sa korisnikom:

1. **Dogovori run tag**: predloži tag na osnovu današnjeg datuma (npr. `mar29`). Grana `autobudget/<tag>` ne sme već da postoji — ovo je novi run.
2. **Kreiraj granu**: `git checkout -b autobudget/<tag>` od trenutnog main-a.
3. **Pročitaj kontekstualne fajlove**: Repo je mali. Pročitaj ove fajlove za puni kontekst:
   - `budžetsko_računovodstvo.md` — početni brainstorming, pojmovi, funkcionalni zahtevi.
   - `program.md` — ovaj fajl. Pravila rada i istraživanja.
4. **Kreiraj `research/` folder** ako ne postoji.
5. **Inicijalizuj results.tsv**: Kreiraj `results.tsv` sa header redom.
6. **Potvrdi i kreni**: Potvrdi da je setup u redu.

Kad dobiješ potvrdu, pokreni istraživačku petlju.

## Cilj

**NE pišeš kod.** Tvoj zadatak je da istražiš domenu i generišeš detaljnu dokumentaciju koja pokriva sve aspekte budžetskog računovodstva u školstvu u Republici Srbiji. Ova dokumentacija će kasnije služiti kao osnova za pisanje formalnog projektnog zadatka za izradu Django aplikacije.

Za svaku temu generiši zaseban `.md` fajl u folderu `research/`.

**Tech stack za koji se priprema dokumentacija: Django (Python), PostgreSQL.**

## Domena

Radiš istraživanje za modul budžetskog računovodstva za obrazovne institucije (osnovne škole, srednje škole, visokoškolske ustanove) u **Republici Srbiji**. Ove institucije su **indirektni korisnici budžetskih sredstava** — finansiraju se iz budžeta Republike Srbije i budžeta jedinica lokalne samouprave, i podležu strogim zakonskim regulativama.

### Ključni koncepti koje moraš istražiti:
- **Kontni plan za budžetski sistem** — prema Pravilniku o standardnom klasifikacionom okviru i Kontnom planu za budžetski sistem ("Sl. glasnik RS")
- **Budžetska klasifikacija** — ekonomska, organizaciona, funkcionalna, programska
- **Plate i doprinosi** — 80-90% budžeta škole, najkompleksniji obračun
- **Trezorski sistem** — Uprava za trezor Ministarstva finansija RS, ISIB sistem
- **Fiskalna godina** — kalendarska godina, svi planovi i izveštaji su godišnji, sa mesečnim/kvartalnim presecima
- **Pravni okvir** — Zakon o budžetskom sistemu, Zakon o računovodstvu, podzakonska akta

### Ključni izvori za pretragu:
- `mfin.gov.rs` — Ministarstvo finansija Republike Srbije
- `pravno-informacioni-sistem.rs` (Pravno-informacioni sistem RS)
- `paragraf.rs` — baza propisa
- `slfrr.rs` ili `nfrr.gov.rs` — finansijsko-računovodstvena regulativa
- `Službeni glasnik RS` — za sve pravilnike i zakone
- `cekos.rs` — obračun plata, doprinosi, porezi
- `infostud.com` — plate, koeficijenti
- `mpn.gov.rs` — Ministarstvo prosvete, nauke i tehnološkog razvoja

## Šta istražuješ i generišeš

Za svaku temu kreiraj detaljan dokument u `research/` folderu:

### FAZA 1 — Pravni i regulatorni okvir
| Fajl | Sadržaj |
|---|---|
| `research/01_pravni_okvir.md` | Svi relevantni zakoni i propisi RS. Zakon o budžetskom sistemu, Zakon o računovodstvu, Zakon o finansiranju lokalne samouprave. Citati ključnih članova. |
| `research/02_kontni_plan.md` | Detaljan kontni plan za budžetski sistem RS. Klase, grupe, sintetički i analitički konta sa objašnjenjima. Primeri knjiženja za škole. |
| `research/03_budzetske_klasifikacije.md` | Ekonomska, organizaciona, funkcionalna i programska klasifikacija. Kako se primenjuju u školstvu. Šifrarnici. |

### FAZA 2 — Finansijski procesi
| Fajl | Sadržaj |
|---|---|
| `research/04_glavna_knjiga.md` | Kako funkcioniše glavna knjiga budžetskog korisnika. Double-entry princip. Dnevnik, analitika, sintetika. Primeri knjiženja za škole. |
| `research/05_budzet_planiranje.md` | Proces planiranja budžeta škole. Ko učestvuje, rokovi, dokumenti, finansijski plan. Rebalans. Primer budžeta osnovne škole. |
| `research/06_budzet_izvrsenje.md` | Praćenje izvršenja budžeta. Zahtevi za plaćanje. Kvote, aproprijacije. Izveštaji. |
| `research/07_trezorski_sistem.md` | Uprava za trezor RS, ISIB sistem. Konsolidovani račun trezora. Kako škole plaćaju preko trezora. Nalozi, odobrenja. |

### FAZA 3 — Obračun plata
| Fajl | Sadržaj |
|---|---|
| `research/08_plate_osnove.md` | Struktura plate u školstvu RS. Osnovica, koeficijenti po zvanjima (Zakon o zaposlenima u javnim službama). Platne grupe i platni razredi. |
| `research/09_plate_dodaci.md` | Svi dodaci na platu: minuli rad (0.4% po godini), dodatak za razrednog starešinu, mentorstvo, rad noću/praznikom. Formule obračuna. |
| `research/10_doprinosi_porezi.md` | Doprinosi iz plate i na platu (PIO 25%, zdravstveno 10.3%, nezaposlenost 0.75%). Porez na zarade 10%. Neoporezivi iznos. Primer kompletnog obračuna bruto-neto. |
| `research/11_bolovanja_odsustva.md` | Obračun bolovanja (prvih 30 dana poslodavac, dalje RFZO). Porodiljsko odsustvo. Godišnji odmor. Plaćeno/neplaćeno odsustvo. |
| `research/12_honorari_ugovori.md` | Ugovori o delu, autorski honorari. Obračun poreza i doprinosa. Specifičnosti za spoljne saradnike u školi. |

### FAZA 4 — Imovina i nabavke
| Fajl | Sadržaj |
|---|---|
| `research/13_javne_nabavke.md` | Zakon o javnim nabavkama RS. Pragovi, postupci (nabavka male vrednosti, otvoreni, restriktivni). Plan nabavki škole. Portal javnih nabavki. |
| `research/14_imovina_amortizacija.md` | Evidencija imovine budžetskog korisnika. Kategorije. Stope amortizacije (Pravilnik). Popis (inventura). Otpis i rashod. |
| `research/15_blagajna_banka.md` | Blagajničko poslovanje škole. Blagajnički maksimum. Izvodi. Format naloga za plaćanje. |

### FAZA 5 — Izveštavanje
| Fajl | Sadržaj |
|---|---|
| `research/16_finansijski_izvestaji.md` | Bilans stanja (Obrazac 1), bilans prihoda i rashoda (Obrazac 2), izveštaj o novčanim tokovima (Obrazac 3), izveštaj o kapitalnim izdacima (Obrazac 5). Rokovi podnošenja Upravi za trezor. |
| `research/17_budzet_izvestaji.md` | Izveštaj o izvršenju budžeta (mesečni, kvartalni, godišnji). Forme. Ko ih prima. Završni račun. |
| `research/18_statisticki_izvestaji.md` | Izveštaji za Republički zavod za statistiku, Ministarstvo prosvete. Obrasci. Rokovi. |

### FAZA 6 — Django specifikacija
| Fajl | Sadržaj |
|---|---|
| `research/19_django_modeli.md` | Predlog Django modela (models.py) za sve module. Relacije, polja, validacije. DecimalField za finansije. |
| `research/20_django_api.md` | Predlog API endpoint-a (DRF ili views). CRUD za sve entitete. Filteri, paginacija. |
| `research/21_django_admin.md` | Predlog Django admin konfiguracije. Inline modeli, filteri, akcije. |
| `research/22_projektni_zadatak.md` | **FINALNI DOKUMENT** — formalni projektni zadatak za izradu aplikacije, sintetizovan iz svega prethodnog. |

## Metrika kvaliteta dokumenta

Svaki dokument se ocenjuje po checklistu. Ovo je tvoj "val_bpb" — kvantitativna mera kvaliteta. Dokument je **kompletiran** kad dobije ocenu 10/10.

```
CHECKLIST (oceni svaki kriterijum sa 0 ili 1):

[ ] 1. ZAKONI:     Citirani konkretni zakoni sa brojem člana i Sl. glasnikom
[ ] 2. FORMULE:    Sve formule obračuna eksplicitno napisane
[ ] 3. PRIMERI:    Minimum 2 numerička primera sa realnim brojevima
[ ] 4. ŠIFRE:      Konkretni šifrarnici, konta, klasifikacije (ne generički)
[ ] 5. PROCEDURE:  Korak-po-korak procedura (ko, šta, kad, koji dokument)
[ ] 6. OBRASCI:    Navedeni zvanični obrasci/forme sa nazivima
[ ] 7. ROKOVI:     Svi rokovi (podnošenja, plaćanja, izveštavanja)
[ ] 8. VEZE:       Cross-reference na druge research dokumente
[ ] 9. DJANGO:     Napomena kako se ovo mapira na Django model/view
[ ] 10. BEZ_RUPA:  Nema "POTREBNA VERIFIKACIJA" ili "TODO" oznaka
```

**Pravilo**: Ako dokument ima ocenu < 8/10, NEMOJ prelaziti na sledeći — doradi ga prvo.

## Template za research dokument

Svaki fajl u `research/` mora pratiti ovaj format:

```markdown
# [Broj]. [Naziv teme]

> Poslednje ažuriranje: [datum]
> Ocena kvaliteta: [X]/10
> Status: draft | review | complete

## Sadržaj
[Kratak opis šta dokument pokriva — 2-3 rečenice]

## Pravni osnov
[Zakoni, pravilnici, članci — sa brojem Sl. glasnika]

## Detaljan opis
[Glavni sadržaj — pojmovi, procedure, pravila]

## Primeri
[Minimum 2 numerička primera sa realnim brojevima]

## Obrasci i dokumenti
[Zvanični obrasci, forme, šabloni koji se koriste]

## Rokovi
[Svi relevantni rokovi]

## Veze sa drugim modulima
[Cross-reference na druge research dokumente: "Videti: 04_glavna_knjiga.md za knjiženje"]

## Napomene za Django implementaciju
[Kako se ovo mapira na modele, view-ove, admin — kratko, bez koda]

## Izvori
[Lista korišćenih izvora sa URL-ovima]
```

## Logovanje rezultata

Kad je iteracija gotova, zapiši u `results.tsv` (tab-separated, NE comma-separated).

```
commit	tema	fajl	status	score	description
```

1. git commit hash (short, 7 chars)
2. naziv teme (npr. kontni_plan, plate_osnove, javne_nabavke)
3. putanja do fajla (npr. research/02_kontni_plan.md)
4. status: `complete` (10/10), `review` (8-9/10), `draft` (<8/10)
5. ocena kvaliteta: X/10 po checklistu
6. kratak opis šta je urađeno u ovoj iteraciji

Primjer:

```
commit	tema	fajl	status	score	description
a1b2c3d	pravni_okvir	research/01_pravni_okvir.md	draft	6/10	inicijalni draft — nedostaju Sl. glasnik reference
b2c3d4e	pravni_okvir	research/01_pravni_okvir.md	review	9/10	dodati članci zakona, cross-ref, ostao 1 TODO
c3d4e5f	pravni_okvir	research/01_pravni_okvir.md	complete	10/10	uklonjen poslednji TODO, verifikovani svi izvori
d4e5f6g	kontni_plan	research/02_kontni_plan.md	draft	5/10	inicijalni draft — treba više primera knjiženja
```

## Petlja istraživanja

Istraživanje se odvija na dediciranoj grani (npr. `autobudget/mar29`).

**Ovo je jedan kontinualan loop — kao kod Karpathy-ja.** Nema odvojenih L1/L2/L3 faza. Agent sam odlučuje da li da piše novi dokument ili da dorađuje postojeći, na osnovu metrike (score).

LOOP ZAUVIJEK:

1. **Proveri stanje**: koji dokumenti postoje u `research/`, koji im je score.
2. **Odluči šta raditi** po ovim pravilima (redom prioriteta):
   - **Ako postoji dokument sa score < 8** → doradi ga (dodaj zakone, primere, cross-ref)
   - **Ako su svi postojeći dokumenti ≥ 8** → kreiraj sledeći dokument po redosledu faza
   - **Ako su svi dokumenti kreirani i ≥ 8** → revizija: cross-reference, konzistentnost brojeva, proveri da se formule poklapaju između dokumenata
   - **Ako je sve ≥ 10 i konzistentno** → napiši/ažuriraj `research/22_projektni_zadatak.md` (finalni dokument)
   - **Ako je i finalni dokument gotov** → ponovo proveri sve od početka sa svežim očima, traži nekonzistentnosti
3. **Istraži temu**:
   - Koristi web pretragu za zakone, propise, stope, obrasce
   - Proveri više izvora — ne oslanjaj se na jedan
   - Traži na: mfin.gov.rs, paragraf.rs, cekos.rs, Sl. glasnik RS
4. **Napiši/dopuni dokument** koristeći template iznad.
5. **Samoevaluacija**: Oceni dokument po checklistu (10 kriterijuma). Budi strog — ako nisi siguran da kriterijum zadovoljen, daj 0.
6. **Commituj** sa opisnim commit message-om koji uključuje score: `"research/02: kontni_plan draft 6/10 — inicijalna struktura"`
7. **Zapiši** u results.tsv (NE commitovati results.tsv).
8. **Nastavi** — nikad ne pitaj korisnika da li da nastaviš.

### Kada se dokument smatra gotovim?

```
Score 10/10  AND  0 "POTREBNA VERIFIKACIJA" oznaka  AND  cross-reference sa svim povezanim dokumentima
```

Tek tada je status `complete`. Sve ispod toga — agent nastavlja da dorađuje.

### Pravilo konzistentnosti brojeva

Kad god dokument sadrži brojeve (stope doprinosa, koeficijente, iznose), proveri da se **isti brojevi pojavljuju identično** u svim dokumentima koji ih referenciraju. Npr:
- Stopa PIO u `10_doprinosi_porezi.md` MORA biti ista kao u `04_glavna_knjiga.md` (primer knjiženja)
- Koeficijent za nastavnika u `08_plate_osnove.md` MORA dati isti neto iznos kad se provuče kroz formulu u `10_doprinosi_porezi.md`

Ako otkriješ nekonzistentnost — to je prioritet, popravi ODMAH pre nego nastaviš dalje.

## Pravila istraživanja

**Šta MOŽEŠ raditi:**
- Kreirati i modifikovati `.md` fajlove u `research/` folderu
- Koristiti web pretragu za zakone, propise, pravilnike, kolektivne ugovore
- Koristiti LLM znanje o računovodstvu, finansijama, Django framework-u
- Commitovati svaki završeni ili dorađeni dokument

**Šta NE MOŽEŠ raditi:**
- Menjati `budžetsko_računovodstvo.md` — to je početni referentni dokument (read-only)
- Pisati Python/Django kod — samo specifikacije i predloge modela u markdown-u
- Izmišljati brojeve za poreske stope ili koeficijente — koristi web pretragu za tačne podatke
- Preskočiti web pretragu za pravne teme — propisi se menjaju, tvoje znanje može biti zastarelo
- Označiti dokument kao `complete` ako ima bilo koji TODO ili nepotvrđen podatak

**Kvalitet dokumenta**:
- Svaki dokument mora biti **detaljan i konkretan** — ne generički
- Uključi **primere** gde god je moguće (primer knjiženja, primer obračuna plate, primer budžeta)
- Citiraj **konkretne zakone i članove** — ne "prema zakonu" nego "prema članu 56. Zakona o budžetskom sistemu (Sl. glasnik RS, br. 54/2009...)"
- Za formule obračuna daj **numeričke primere** sa realnim brojevima
- Svi finansijski iznosi u **dinarima (RSD)**

**Kriterij kompletnosti**: Dokument je kompletiran kad sadrži dovoljno informacija da programer koji nikad nije radio sa budžetskim računovodstvom može na osnovu njega napisati funkcionalan Django modul — bez guglanja.

## Prioriteti i redosled

```
FAZA 1 — Pravni temelj (OBAVEZNO PRVO)
├── 01_pravni_okvir             ← zakoni i propisi RS
├── 02_kontni_plan              ← klase, grupe, analitička konta
└── 03_budzetske_klasifikacije  ← ekonomska, org., funkcionalna, programska

FAZA 2 — Finansijski procesi
├── 04_glavna_knjiga            ← double-entry, dnevnik, salda
├── 05_budzet_planiranje        ← finansijski plan, rokovi, dokumenti
├── 06_budzet_izvrsenje         ← praćenje, aproprijacije, kvote
└── 07_trezorski_sistem         ← Uprava za trezor, ISIB, KRT

FAZA 3 — Plate i doprinosi
├── 08_plate_osnove             ← osnovice, koeficijenti, zvanja
├── 09_plate_dodaci             ← minuli rad 0.4%, razredno starešinstvo
├── 10_doprinosi_porezi         ← PIO 25%, zdr. 10.3%, porez 10%
├── 11_bolovanja_odsustva       ← naknade, RFZO, trajanja
└── 12_honorari_ugovori         ← ugovori o delu, autorski

FAZA 4 — Imovina i nabavke
├── 13_javne_nabavke            ← ZJN, pragovi, postupci, portal
├── 14_imovina_amortizacija     ← registar, stope, popis
└── 15_blagajna_banka           ← gotovina, izvodi, nalozi

FAZA 5 — Izveštavanje
├── 16_finansijski_izvestaji    ← Obrasci 1-5, rokovi
├── 17_budzet_izvestaji         ← izvršenje, završni račun
└── 18_statisticki_izvestaji    ← RZS, Ministarstvo prosvete

FAZA 6 — Django specifikacija (FINALNA FAZA)
├── 19_django_modeli            ← models.py predlog
├── 20_django_api               ← views/DRF predlog
├── 21_django_admin             ← admin konfiguracija
└── 22_projektni_zadatak        ← FINALNI projektni zadatak
```

## NIKAD NE STAJ

Jednom kad petlja istraživanja počne (nakon inicijalnog setup-a), NE zaustavljaj se da pitaš korisnika da li da nastaviš. NE pitaj "da li da nastavim?" ili "je li ovo dobra tačka za pauzu?". Korisnik možda spava ili nije za računarom i očekuje da nastavljaš da radiš **neograničeno** dok te ručno ne zaustavi. Ti si autonoman.

Loop nikad ne staje. Kad su svi dokumenti na 10/10:
- Cross-referenciraj dokumente međusobno
- Proveri konzistentnost svih brojeva
- Dopuni primere
- Poboljšaj finalni projektni zadatak
- Traži edge cases i specifičnosti koje si propustio

Korisnik se može vratiti i naći kompletnu, konzistentnu, detaljnu dokumentaciju za projektni zadatak — sa svim zakonima, formulama, primerima i Django specifikacijama.
