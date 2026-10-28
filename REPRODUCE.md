# How this repository was made (Republic of the Congo)

This file is written by the build on 2026-10-28, the day the source data was retrieved. Everything below is enough to rebuild this repository hash for hash.

## Sources

| Source | Address | Retrieved | Requests | Licence |
| --- | --- | --- | ---: | --- |
| Journal officiel de la République du Congo (SGG, sgg.cg) | <https://sgg.cg> | 2026-10-28 | 9 | Official texts; no licence stated on sgg.cg (Mentions légales checked). |

Every response is cached by the sha256 of its URL, and the table above lists every source with its retrieval date. Lexifina keeps its fetch scripts privately; `tools/parse.py` reads only the cache and writes `corpus.json`, so the same cache always gives the same corpus.

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
- 0 commits on the branch `futur`: laws not yet in force on 2026-10-28.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 3 laws in the record.
- 6 tags.

## Dates

Each commit is dated at noon (Africa/Brazzaville) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: No general Congolese statute fixing when laws take effect was found on the SGG site. Laws end "sera publiée au Journal officiel et exécutée comme loi de l’Etat"; where a law names no date of its own, this build dates it by its publication in the Journal officiel. The Constitution of 2015 takes effect on promulgation (art. 246). https://sgg.cg/JO/2015/congo-jo-2015-08-sp.pdf

## Commands, in order

```sh
# fill the cache from the sources listed above (network; Lexifina's fetch scripts are kept privately)
python -X utf8 tools/parse.py                  # cache -> corpus.json (no network)
python -X utf8 tools/build.py <folder> --repo <empty folder> --docs-date 2026-10-28
python -X utf8 tools/check_repo.py <repo> --corpus <folder>/corpus.json --write
python -X utf8 tools/build.py <folder> --repo <another empty folder> --docs-date 2026-10-28 --compare <repo>
```

In the main Lexifina repository these files live as follows:
- `fetch.py`, `parse.py` and `repo/`: in `scripts/republic-of-congo-law/`.
- `build.py`, `check_repo.py` (`check.py` there) and `on.py`: in `scripts/gitlaw_common/`, with the corpus format in `SCHEMA.md`.

## Exact inputs

- `corpus.json` sha256 `404eb759b64f3329d05fe33d34d81ee6754fedc4f7e191e69daca568bb3ea626` (306072 bytes)
- Script blob hashes (`git hash-object`):

| Script | Blob |
| --- | --- |
| build.py | `2bfc4ac9df193a7be844556d7f69cdb9d93ec3f2` |
| check.py | `cd346c7ff9996d450240e3bab52bcae03b2bc865` |
| on.py | `644a6c0857fbcc72562032b58d57aa113fee0641` |
| fetch.py | `4ec60638113a804390c0692a872de4b71fe3149b` |
| parse.py | `7b139ed8d5732ad0552bae2bb3be97c15f54f247` |

- Tools:
  - Python 3.14.0
  - git version 2.52.0.windows.1
  - curl 8.21.0 (Windows) libcurl/8.21.0 Schannel zlib/1.3.2 WinIDN WinLDAP

## Checks

3 versions of 2 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

Not yet run for this build.

These results are from the check run on the build before this one, from the same corpus.

## Decisions made by hand

- Text is read only from the Journal officiel PDFs’ text layer; the SGG HTML consolidation of the Constitution differs from the JO in small editorial ways (it drops some figures in brackets such as "(90)" and recases words), so it is used only as a cross-check.
- Constitution in force 2015-11-06: art. 246 puts it in force on promulgation; the JO édition spéciale n° 8 that prints "Le Président de la République promulgue la Constitution" is dated vendredi 6 novembre 2015, and no other promulgation date is printed.
- Loi constitutionnelle n° 2-2022 dated 2022-01-10 and Loi n° 29-2019 dated 2019-11-07: neither names its own commencement day, so each is dated by its JO issue (default rule above).
- Loi n° 29-2019 art. 100 gives existing processing one or two years from entry into force to comply; this is a compliance period, not a commencement, so it is not encoded in applies.
- Words hyphenated at a JO line end are rejoined without the hyphen unless one side is a known compound part (quatre-vingt, celui-ci, peut-être and the like); see jo_text.KEEP_HYPHEN_LEFT/RIGHT.
- Titles, sub-titles and chapter headings are not units; each unit is the preamble or one article, one paragraph or list item per line.
- JO 2015 prints "Articles 194 :" (a typo for Article 194); the parser reads it as Article 194.
- Code pénal not built: SGG lists the Code pénal du Congo as the French code applied by arrêté of 13 February 1882, not published in the JO and with no text on sgg.cg; amendments are scattered ordinances (e.g. Ord. 62-13). Skipped under the 45-minute rule.
- Code de la famille (1984) not built: the SGG PDF is a scan with no text layer (no OCR by rule).

## What AI did and did not do

The fetch, parse and check scripts were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above, through code that anyone can rerun.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- none: no model produced or edited any text or date at data-build time. The parser and checks were written by Claude Code (claude-opus-5-5).
