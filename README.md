# Viëtor 1921 – German pronunciation dictionary as open data

[English](#english) · [Deutsch](#deutsch)

## English

A machine-readable edition of the word list of **Wilhelm Viëtor, *Deutsches Aussprachewörterbuch*, 3rd edition, revised
by Ernst A. Meyer, Leipzig: O. R. Reisland 1921**. 36,779 entries, each with the phonetic transcription as printed,
the stressed syllable and the length of the stressed vowel.

**License: CC0 1.0** (see `LICENSE`). Use it for anything, no attribution required. A mention is appreciated.

**Why it is free.** Viëtor died in 1918, Meyer on 1 May 1953, so the book has been in the public domain since
1 January 2024. The source is the scan at the Internet Archive,
[`deutschesausspra00viuoft`](https://archive.org/details/deutschesausspra00viuoft) (University of Toronto). The dataset
contains only what is printed in that book: headword, transcription, and what follows from them. Nothing is taken from
a modern dictionary.

### File

`vietor-1921.tsv` – tab-separated, UTF-8, one row per entry. Homographs and variants appear as separate rows.

| Column | Meaning |
|---|---|
| `word` | headword as printed, in 1921 spelling (Narziß, Eßlingen) |
| `transcription` | Viëtor's transcription (IPA as of 1921): `ˈ` stress before the syllable, `:` long, `·` half-long, `ʾ` glottal stop, `ĭ` non-syllabic, `[..]` optional sounds, `(ˈ)` optional secondary stress |
| `stress_syllable_phonetic` | stressed syllable in the transcription (1 = first). Without a stress mark, the first full syllable (not ə), as Viëtor's preface specifies. With two stress marks (equal stress), the first |
| `syllables_phonetic` | number of syllables in the transcription |
| `stress_syllable_spelling` | stressed syllable counted on the spelling (vowel nuclei: äu eu au ei ai ey ay ie aa ee oo, otherwise single vowels). Empty if the two counts do not match |
| `vowel_length` | vowel of the stressed syllable: `L` long, `S` short, `D` diphthong |
| `pdf_page`, `book_page`, `line` | location in the scan |
| `reading` | how the line was read, see below |
| `flags` | notes from the checks, comma-separated, see below |

### How it was made

Every printed line of the word list (468 pages, 48,742 lines) was read three times, independently:
by two language models looking at the line image (A = Claude Sonnet, B = Claude Opus) and by a Tesseract model trained
on this book (M).

| `reading` | Meaning | Entries |
|---|---|---|
| `ABM` | all three readings identical | 29,308 |
| `AB` | both language models agree, the trained model differs | 5,166 |
| `BM` / `AM` | one language model and the trained model agree | 1,850 / 125 |
| `arbitrated` | all three differ; two arbiters (Opus, Sonnet) agreed independently on the enlarged image | 266 |
| `disputed` | no agreement – use with care | 64 |

The stressed syllable is derived from the transcription. A hand reading of 100 entries from two pages served as
a check: 97 of them were found, and all 97 match in stressed syllable and vowel length.

| `flags` | Meaning | Entries |
|---|---|---|
| `syllable-count:s/p` | syllable count of the spelling (s) differs from the transcription (p) | 2,190 |
| `variant` | Viëtor gives several pronunciations; the first complete one is used | 2,005 |
| `second-stress:n` | a second, equally strong stress on syllable n | 1,465 |
| `onset` | first sound does not match the first letter – transcription probably assigned to the wrong headword | 419 |
| `oe-rule` | short ö: a reading of ə corrected to œ because the headword has ö (Viëtor writes ə only for unstressed e) | 6 |
| others | check rules (stress mark without a vowel, length on schwa, ü without y, …) | < 200 |

### Known limits

- Pronunciation and spelling are those of 1921 (stage pronunciation). Some words have changed since (Kanu, Sahara).
- Viëtor deliberately does not mark secondary stress in compounds.
- Short ö (printed as a barred ring) and ə differ by one or two pixels in the scan; the `oe-rule` repairs the cases
  where the headword shows ö. The superscript ¹ marking homographs is unreliable.
- Rows flagged `onset` or `disputed` should be left out for most purposes.

### Use

The dataset is used in KlangFeder, a lyrics tool. There it serves as a second pronunciation lexicon behind ipa-dict,
for stress and rhyme, filtered as above.

---

## Deutsch

Eine maschinenlesbare Fassung des Wörterverzeichnisses aus **Wilhelm Viëtor, *Deutsches Aussprachewörterbuch*,
3. Auflage, besorgt von Ernst A. Meyer, Leipzig: O. R. Reisland 1921**. 36 779 Einträge, je mit der gedruckten
Lautschrift, der betonten Silbe und der Länge des betonten Vokals.

**Lizenz: CC0 1.0** (siehe `LICENSE`). Frei für jeden Zweck, ohne Namensnennung. Ein Hinweis freut uns.

**Warum frei.** Viëtor starb 1918, Meyer am 1. 5. 1953; das Buch ist seit dem 1. 1. 2024 gemeinfrei. Grundlage ist der
Scan im Internet Archive, [`deutschesausspra00viuoft`](https://archive.org/details/deutschesausspra00viuoft)
(University of Toronto). Der Datensatz enthält nur, was in diesem Buch steht: Stichwort, Lautschrift und was daraus
folgt. Aus heutigen Wörterbüchern ist nichts übernommen.

### Datei

`vietor-1921.tsv` – Tabulator-getrennt, UTF-8, eine Zeile je Eintrag; Homographe und Varianten stehen mehrfach.

| Spalte | Bedeutung |
|---|---|
| `word` | Stichwort wie gedruckt, Rechtschreibung von 1921 (Narziß, Eßlingen) |
| `transcription` | Viëtors Lautschrift (IPA von 1921): `ˈ` Ton vor der Silbe, `:` lang, `·` halblang, `ʾ` Knacklaut, `ĭ` unsilbig, `[..]` wahlweise Laute, `(ˈ)` wahlweiser Nebenton |
| `stress_syllable_phonetic` | betonte Silbe in der Lautschrift (1 = erste). Ohne Tonstrich die erste volle Silbe (nicht ə), wie im Vorwort festgelegt. Bei zwei Tonstrichen (gleich starker Ton) der erste |
| `syllables_phonetic` | Zahl der Silben der Lautschrift |
| `stress_syllable_spelling` | betonte Silbe, gezählt an der Schreibung (Silbenkerne äu eu au ei ai ey ay ie aa ee oo, sonst Einzelvokal). Leer, wenn die Zählungen nicht zusammenpassen |
| `vowel_length` | Vokal der betonten Silbe: `L` lang, `S` kurz, `D` Zwielaut |
| `pdf_page`, `book_page`, `line` | Fundstelle im Scan |
| `reading` | wie die Zeile gelesen wurde (Tabelle im englischen Teil): `ABM` alle drei Lesungen gleich, `AB` beide Sprachmodelle gleich, `BM`/`AM` ein Sprachmodell und das Lesemodell gleich, `arbitrated` per Schiedsrunde entschieden, `disputed` keine Einigung |
| `flags` | Befunde der Prüfung (Tabelle im englischen Teil) |

**Verfahren.** Jede Druckzeile (468 Seiten, 48 742 Zeilen) wurde dreimal unabhängig gelesen: von zwei Sprachmodellen
am Zeilenbild (A = Claude Sonnet, B = Claude Opus) und von einem auf dieses Buch nachgelernten Tesseract-Modell (M).
Strittige Zeilen entschieden zwei Schiedsrichter am vergrößerten Bild. Gegen eine Handlesung von 100 Einträgen:
97 gefunden, alle 97 richtig in Silbe und Länge.

**Grenzen.** Aussprache und Rechtschreibung von 1921 (Bühnenaussprache); manches hat sich seither geändert. Nebenton
in Zusammensetzungen bezeichnet Viëtor absichtlich nicht. Kurzes ö und ə unterscheiden sich im Scan um 1–2 Pixel; die
`oe-rule` berichtigt die Fälle, in denen das Stichwort ö zeigt. Die hochgestellte ¹ der Homographe ist unsicher.
Zeilen mit `onset` oder `disputed` lässt man für die meisten Zwecke besser weg.
