# How this repository was made (Republic of the Congo)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Journal officiel de la République du Congo (SGG, sgg.cg) | <https://sgg.cg> | 2026-10-28 | Official texts; no licence stated on sgg.cg (Mentions légales checked). |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | Constitution de la République du Congo du 25 octobre 2015 | 2 | 2015-11-06 to 2022-01-10 |
| `donnees-personnelles` | Loi n° 29-2019 du 10 octobre 2019 portant protection des données à caractère personnel | 1 | 2019-11-07 to 2019-11-07 |

The build made 3 commits:

| Commits | Kind |
| ---: | --- |
| 2 | first version of an act |
| 1 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `futur`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 3 laws in the record.
- 6 tags.

## Dates

Each commit is dated at noon (Africa/Brazzaville) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: No general Congolese statute fixing when laws take effect was found on the SGG site. Laws end "sera publiée au Journal officiel et exécutée comme loi de l’Etat"; where a law names no date of its own, this build dates it by its publication in the Journal officiel. The Constitution of 2015 takes effect on promulgation (art. 246). https://sgg.cg/JO/2015/congo-jo-2015-08-sp.pdf

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `84be98e413855bf6ed77c5d1154623caa2b017b787feca577d7ce8a64a345967` (306072 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3e59cb6f05eccb94a9ec14431a7f6781221e83ef`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

3 versions of 2 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- Text is read only from the Journal officiel PDFs’ text layer; the SGG HTML consolidation of the Constitution differs from the JO in small editorial ways (it drops some figures in brackets such as "(90)" and recases words), so it is used only as a cross-check.
- Constitution in force 2015-11-06: art. 246 puts it in force on promulgation; the JO édition spéciale n° 8 that prints "Le Président de la République promulgue la Constitution" is dated vendredi 6 novembre 2015, and no other promulgation date is printed.
- Loi constitutionnelle n° 2-2022 dated 2022-01-10 and Loi n° 29-2019 dated 2019-11-07: neither names its own commencement day, so each is dated by its JO issue (default rule above).
- Loi n° 29-2019 art. 100 gives existing processing one or two years from entry into force to comply; this is a compliance period, not a commencement, so it is not encoded in applies.
- Words hyphenated at a JO line end are rejoined without the hyphen unless one side is a known compound part (quatre-vingt, celui-ci, peut-être and the like); see Lexifina's code/RIGHT.
- Titles, sub-titles and chapter headings are not units; each unit is the preamble or one article, one paragraph or list item per line.
- JO 2015 prints "Articles 194 :" (a typo for Article 194); the parser reads it as Article 194.
- Code pénal not built: SGG lists the Code pénal du Congo as the French code applied by arrêté of 13 February 1882, not published in the JO and with no text on sgg.cg; amendments are scattered ordinances (e.g. Ord. 62-13). Skipped under the 45-minute rule.
- Code de la famille (1984) not built: the SGG PDF is a scan with no text layer (no OCR by rule).

## Added 2026-11-27: more sources, type/year layout

- Layout: one pure-rename commit moved `donnees-personnelles/` to
  `lois/2019/29-2019-portant-protection-des-donnees-a-caractere-personnel/`; new acts go under `lois/`, `ordonnances/`,
  `decrets/`, `arretes/` by year, and `codes/<code>/` (see `STRUCTURE.md`). `corpus.json` lists the acts
  (`cg/national/acts`).
- Sources: FAOLEX records for Congo (record URLs from FAOLEX's public sitemaps `faolex.fao.org/sitemaps/documents-*.xml`,
  slugs ending `-cog-<year>`; the record's own JSON gives the PDF and the date of the text); the Internet Archive copies of
  economie.gouv.cg/sites/default/files/Documentation/ (CDX listing; the host times out, so the dead-site rule applies);
  WIPO Lex profile CG; PDFs on cour-constitutionnelle.cg (its public `/api/documents` listing).
- Added 2026-11-27 (runner `cg_build.py`, `web_items` / `cemac_items`): the finances.gouv.cg documentation listing
  (`/fr/documentation?term_node_tid_depth=<category>`, categories Lois, Décrets, Arrêtés, Ordonnances, Directives,
  Règlements; title from the listing, or from page 1 when the listing gives no number/date); PDFs listed by the
  Internet Archive CDX index for finances.gouv.cg and sante.gouv.cg (fetched live), and for assemblee-nationale.cg,
  budget.gouv.cg and commerce.gouv.cg (fetched from the Wayback copy: the files are no longer served); the WordPress
  media lists (`/wp-json/wp/v2/media?mime_type=application/pdf`) of hydrocarbures.gouv.cg, primature.gouv.cg,
  gouvernement.cg and cemac.int. Title from the file name or page 1 (the file name wins when they disagree).
  CEMAC acts go under `cemac/reglements|directives|actes-additionnels/<year>/`, dated on the day in their title.
  Nominations and individual decisions are not taken; scans without a text layer are held (no OCR).
- sgg.cg is not used any more: its legal notice requires prior express authorisation for any reproduction (decision
  recorded 2026-11-27; the three acts already taken from its Journal officiel stay).
- Text: the PDF's own text layer (PyMuPDF), one file per article, visas in `visas.md`, signatures in `signatures.md`.
  No OCR of our own: PDFs with fewer than 250 characters a page, or whose layer reads badly (fewer than 90% clean
  words), are held. Layers a publisher laid over a scan are tagged `Text-source: publisher OCR`; they are not proofread.
- Dates: the day of the text in its title (promulgation/signature), noon Africa/Brazzaville, with `In-force` and
  `In-force-basis` trailers; failing a date in the title, the FAOLEX record's full `date_of_text`. Texts whose title and
  FAOLEX date disagree by more than 400 days, or with no full date, are held. Before 1970: committed at 1970-01-01 with
  the real day in the subject and `In-force`.
- Code pénal: FAOLEX record LEX-FAOC244284, the Ministry of Justice's "Codes d'audience" (Giraf), brought up to date on
  31 October 1998 (FAOLEX `date_of_consolidation`): one as-at version dated that day; the layer is the scanner's OCR
  (`Text-source: publisher OCR`), held to a lower 80% clean-word floor and not proofread.
- Duplicates: one act per kind and number (arrêtés: per number and year); the first source in the order Cour
  constitutionnelle / WIPO Lex, FAOLEX, economie.gouv.cg wins.
- Runner: `scripts/republic-of-congo-law/runner/cg_build.py` (detached, below-normal priority, about one request a second
  per host, back-off on timeouts and 5xx, stop on 403/429/challenge).

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- none: no model produced or edited any text or date at data-build time. The parser and checks were written by Claude Code (claude-opus-5-5).
