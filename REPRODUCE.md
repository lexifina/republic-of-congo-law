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

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- none: no model produced or edited any text or date at data-build time. The parser and checks were written by Claude Code (claude-opus-5-5).
