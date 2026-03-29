# autobudget — Autonomno istraživanje modula za budžetsko računovodstvo u školstvu

Ovo je eksperiment u kojem LLM autonomno istražuje, dizajnira i iterativno gradi modul za budžetsko računovodstvo u obrazovnim institucijama.

## Setup

Za pokretanje novog eksperimenta, dogovori se sa korisnikom:

1. **Dogovori run tag**: predloži tag na osnovu današnjeg datuma (npr. `mar29`). Grana `autobudget/<tag>` ne smije već postojati — ovo je svježi run.
2. **Kreiraj granu**: `git checkout -b autobudget/<tag>` od trenutnog main-a.
3. **Pročitaj kontekstualne fajlove**: Repo je mali. Pročitaj ove fajlove za puni kontekst:
   - `brainstorming/budžetsko_računovodstvo.md` — domena, pojmovi, funkcionalni zahtjevi, pravni okvir.
   - `brainstorming/program.md` — ovaj fajl. Pravila rada i eksperimentisanja.
   - `src/models/` — data modeli (šeme baze). Ovo je fajl koji kreiraš i modificiraš.
   - `src/api/` — API endpointi. Ovo kreiraš i modificiraš.
   - `src/services/` — poslovna logika. Ovo kreiraš i modificiraš.
4. **Provjeri okruženje**: Provjeri da je baza podataka dostupna i da su dependencies instalirani. Ako ne, reci korisniku da pokrene `npm install` ili ekvivalent.
5. **Inicijaliziraj results.tsv**: Kreiraj `results.tsv` sa header redom. Baseline će se zabilježiti nakon prvog modula.
6. **Potvrdi i kreni**: Potvrdi da je setup u redu.

Kad dobiješ potvrdu, pokreni eksperimentaciju.

## Domena

Radiš na modulu za budžetsko računovodstvo za obrazovne institucije (osnovne škole, srednje škole, visokoškolske ustanove). Ove institucije su **budžetski korisnici** — finansiraju se iz javnih sredstava i podliježu strogim zakonskim regulativama.

### Ključni koncepti koje moraš razumjeti:
- **Kontni plan za budžetske korisnike** (klase 0-9) — temelj cijelog modula
- **Budžetska klasifikacija** — ekonomska, organizaciona, funkcionalna, programska
- **Plate i doprinosi** — 80-90% budžeta škole, najkompleksniji obračun
- **Trezorski sistem** — škole ne plaćaju direktno, sve ide preko trezora
- **Fiskalna godina** — svi planovi i izvještaji su godišnji, sa mjesečnim/kvartalnim presjecima

## Eksperimentacija

Svaki eksperiment se fokusira na **jedan modul ili podmodul** iz sistema. Radi iterativno — prvo data model, pa servisni sloj, pa API, pa validacija.

**Šta MOŽEŠ raditi:**
- Kreirati i modificirati fajlove u `src/` — modeli, servisi, API, utils
- Kreirati migracije baze podataka
- Pisati unit i integration testove
- Koristiti LLM za istraživanje pravnih propisa i računovodstvenih standarda
- Predlagati šemu baze, API dizajn, poslovnu logiku

**Šta NE MOŽEŠ raditi:**
- Mijenjati `brainstorming/budžetsko_računovodstvo.md` — to je referentni dokument (read-only)
- Instalirati nove pakete bez eksplicitnog odobrenja korisnika
- Preskočiti validaciju podataka — budžetski podaci moraju biti tačni do zadnje pare
- Ignorisati audit trail — svaka promjena finansijskih podataka mora biti logovana
- Brisati ili mijenjati zatvorene fiskalne periode

**Cilj je jednostavan: napraviti funkcionalan, korektan i jednostavan modul koji zadovoljava zahtjeve iz brainstorming dokumenta.** Prioritet je:

1. **Korektnost** — računovodstveni podaci moraju biti 100% tačni. Bilans se mora poklapati. Duguje = Potražuje, uvijek.
2. **Usklađenost** — modul mora poštovati zakonske propise i računovodstvene standarde.
3. **Jednostavnost** — manje koda je bolje. Ne pretjerivati sa apstrakcijama.
4. **Proširivost** — kontni plan i formule moraju biti konfigurabilan, jer se propisi mjenjaju.

**Kriterij jednostavnosti**: Isto kao kod treniranja modela — ako dodaješ kompleksnost, mora donijeti jasnu vrijednost. 20 linija koda za edge case koji se dešava jednom godišnje? Vjerovatno ne. Konfigurabilan kontni plan umjesto hardkodiranog? Obavezno — propisi se mijenjaju.

**Prva iteracija**: Uvijek počni sa data modelom za kontni plan i glavnu knjigu — to je fundament svega.

## Output format

Nakon svake iteracije, modul se validira ovako:

```
---
modul:              kontni_plan
status:             pass | fail | partial
test_coverage:      85%
api_endpoints:      5
db_migrations:      2
validation_errors:  0
bilans_check:       BALANCED | UNBALANCED
complexity_score:   low | medium | high
---
```

Možeš izvući ključne metrike:

```
grep "^status:\|^bilans_check:\|^validation_errors:" iteration.log
```

## Logovanje rezultata

Kad je iteracija gotova, zapiši u `results.tsv` (tab-separated, NE comma-separated).

TSV ima header red i 6 kolona:

```
commit	modul	status	bilans_check	complexity	description
```

1. git commit hash (short, 7 chars)
2. naziv modula (npr. kontni_plan, glavna_knjiga, plate)
3. status: `keep`, `discard`, ili `fail`
4. bilans_check: `BALANCED`, `UNBALANCED`, ili `N/A`
5. complexity: `low`, `medium`, `high`
6. kratak opis šta je ova iteracija pokušala

Primjer:

```
commit	modul	status	bilans_check	complexity	description
a1b2c3d	kontni_plan	keep	N/A	low	baseline — CRUD za kontni plan sa 9 klasa
b2c3d4e	glavna_knjiga	keep	BALANCED	medium	dnevnik knjiženja sa double-entry validacijom
c3d4e5f	plate_obracun	keep	BALANCED	high	obračun plata sa koeficijentima i doprinosima
d4e5f6g	plate_bolovanje	fail	UNBALANCED	high	obračun bolovanja — formula za refundaciju neispravna
e5f6g7h	plate_bolovanje	keep	BALANCED	medium	fix formule — pojednostavljen pristup
```

## Petlja eksperimentacije

Eksperiment se odvija na dediciranoj grani (npr. `autobudget/mar29`).

LOOP ZAUVIJEK:

1. **Provjeri git stanje**: trenutna grana/commit, šta je urađeno do sad.
2. **Odaberi sljedeći modul/podmodul** iz prioritetne liste:
   - Faza 1: kontni_plan → glavna_knjiga → dnevnik_knjiženja → bilans_stanja → bilans_uspjeha
   - Faza 2: budžet_plan → budžet_izvršenje → plate_obračun → plate_doprinosi → banka_export
   - Faza 3: javne_nabavke → imovina_registar → amortizacija → blagajna → bankovni_izvodi
   - Faza 4: trezor_integracija → custom_izvještaji → dashboard → notifikacije
3. **Istraži domenu** — ako ti treba kontekst o specifičnom propisu ili formuli, koristi LLM znanje i web pretragu.
4. **Implementiraj** — data model, servis, API, testovi.
5. **Validiraj**:
   - Pokreni testove: `npm test > iteration.log 2>&1`
   - Provjeri bilans: Duguje == Potražuje za svaki nalog
   - Provjeri API: svaki endpoint vraća očekivane rezultate
6. **Zapiši rezultat** u results.tsv (NE commitovati results.tsv, drži ga untracked)
7. **Ako je validacija prošla** (status: pass/keep) — commituj i nastavi dalje
8. **Ako je validacija pala** (status: fail) — analiziraj grešku:
   - Ako je bug u kodu — popravi i ponovo testiraj
   - Ako je konceptualni problem — zapiši kao `discard`, git reset i pokušaj drugi pristup
   - Ako ne možeš riješiti nakon 3 pokušaja — zapiši kao `fail`, revert i nastavi sa sljedećim modulom

### Pravila za računovodstvenu korektnost:

- **Double-entry princip**: Svako knjiženje MORA imati duguje i potražuje stranu. Zbir duguje MORA biti jednak zbiru potražuje. Nema izuzetaka.
- **Zatvoreni periodi**: Jednom zatvoren mjesec/godina se NE MOŽE mijenjati. Korekcije se rade kroz nova knjiženja u tekućem periodu.
- **Decimalna preciznost**: Svi finansijski iznosi na 2 decimale. Nikad floating point — koristi integer (u fenigima/centima) ili Decimal tip.
- **Valuta**: Podrazumijevana valuta je BAM (konvertibilna marka). Sistem mora podržavati šifru valute za buduću proširivost.
- **Redni brojevi**: Nalozi u glavnoj knjizi imaju kontinuirani redni broj unutar fiskalne godine. Nema rupa u sekvenci.
- **Audit trail**: Svaki zapis ima created_by, created_at, updated_by, updated_at. Finansijski zapisi imaju i full change history.

### Pravila za plate u školstvu:

- Plata = osnovica * koeficijent + dodaci (minuli rad, razredništvo, mentorstvo, itd.)
- Minuli rad = 0.5% po godini staža (ili prema kolektivnom ugovoru)
- Doprinosi se računaju NA platu (poslodavac) i IZ plate (zaposleni)
- Bolovanje: prvih 42 dana na teret poslodavca, nakon toga na teret fonda
- Porodiljsko: 100% plate, na teret budžeta ili fonda (zavisno od propisa)
- Topli obrok, prevoz, regres — prema kolektivnom ugovoru

## Prioriteti i redoslijed

```
FAZA 1 — Fundament (OBAVEZNO PRVO)
├── kontni_plan        ← konfigurabilna šema sa 9 klasa i podkontima
├── glavna_knjiga      ← double-entry knjiženje, dnevnik, salda
├── bilans_stanja      ← automatsko generisanje iz glavne knjige
└── bilans_uspjeha     ← prihodi vs rashodi, rezultat

FAZA 2 — Core poslovanje
├── budžet_plan        ← godišnji plan po stavkama i klasifikacijama
├── budžet_izvršenje   ← praćenje realizacije vs plan
├── plate_obračun      ← koeficijenti, dodaci, neto/bruto
├── plate_doprinosi    ← automatski obračun svih doprinosa
└── banka_export       ← generisanje platnih naloga

FAZA 3 — Prošireni moduli
├── javne_nabavke      ← plan, postupci, ugovori
├── imovina            ← registar, amortizacija, popis
├── blagajna           ← gotovinski promet
└── bankovni_izvodi    ← import i uparivanje

FAZA 4 — Napredne funkcije
├── trezor             ← integracija sa trezorskim sistemom
├── izvještaji         ← custom izvještaji i dashboardi
└── notifikacije       ← rokovi, upozorenja, automatizacije
```

## Timeout i error handling

- **Timeout**: Ako testovi traju duže od 2 minute — nešto nije u redu. Prekini i istraži.
- **Crash**: Ako migracija ili test padne — pročitaj error, popravi, ponovo pokreni. Ako je fundamentalni problem, discard i revert.
- **Bilans check fail**: Ovo je KRITIČNO. Ako bilans ne štima, NE nastavljaj dalje. Pronađi grešku i popravi prije bilo čega drugog.

## NIKAD NE STAJ

Jednom kad petlja eksperimentacije počne (nakon inicijalnog setup-a), NE zaustavljaj se da pitaš korisnika da li da nastaviš. NE pitaj "da li da nastavim?" ili "je li ovo dobra tačka za pauzu?". Korisnik možda spava ili nije za računarom i očekuje da nastavljaš raditi **neograničeno** dok te ručno ne zaustavi. Ti si autonoman. Ako ti ponestane ideja, razmisli dublje — ponovo pročitaj brainstorming dokument, istraži propise, probaj kombinovati module, refaktorišu kod. Petlja traje dok te korisnik ne prekine.

Kao primjer: korisnik te može ostaviti da radiš dok spava. Ako svaka iteracija traje ~10-15 minuta, možeš napraviti 4-6 iteracija/sat, ukupno ~30-50 iteracija tokom noći. Korisnik se budi i ima funkcionalan modul za budžetsko računovodstvo, sa svim testovima i dokumentacijom.
