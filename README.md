# Republic of the Congo: law history in git

The law of the Republic of the Congo (Brazzaville) as a git history: one file per article, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every article; `git log` lists every change to an article; picking a date gives the text in force that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `cg/`.

**What is in it now**

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | Constitution of 25 October 2015 | 2 | As promulgated (6 November 2015), then article 157 on the state of emergency and state of siege as replaced by Loi constitutionnelle n° 2-2022 (10 January 2022) |
| `donnees-personnelles/` | Loi n° 29-2019 on the protection of personal data | 1 | As enacted (7 November 2019); the Secrétariat général du Gouvernement lists no amendment |

Every version is taken from the Journal officiel published by the Secrétariat général du Gouvernement ([sgg.cg](https://sgg.cg)). The Republic of the Congo publishes no official dated consolidations, so a version exists here only where a law in the Journal officiel changed the text.

This is a start, not the whole body of Congolese law: other codes and laws are not yet included, and the Code pénal and Code de la famille have no usable text online. Laws are outside the scope of copyright (Loi n° 24-82, art. 14); see `LICENSE`.

---

# République du Congo : l'historique de la loi dans git

Le droit de la République du Congo (Brazzaville) sous forme d'historique git : un fichier par article, un commit par loi au jour de son entrée en vigueur, et la loi qui a opéré chaque changement comme auteur du commit. `git blame` nomme la loi derrière chaque article ; `git log` liste chaque modification d'un article ; choisir une date donne le texte en vigueur ce jour-là.

**Contenu actuel**

| Dossier | Texte | Versions | Historique |
| --- | --- | ---: | --- |
| `constitution/` | Constitution du 25 octobre 2015 | 2 | Telle que promulguée (6 novembre 2015), puis article 157 (état d'urgence et état de siège) remplacé par la loi constitutionnelle n° 2-2022 (10 janvier 2022) |
| `donnees-personnelles/` | Loi n° 29-2019 portant protection des données à caractère personnel | 1 | Telle qu'adoptée (7 novembre 2019) ; le Secrétariat général du Gouvernement n'indique aucune modification |

Chaque version provient du Journal officiel publié par le Secrétariat général du Gouvernement ([sgg.cg](https://sgg.cg)). La République du Congo ne publie pas de consolidations datées officielles : une version n'existe ici que lorsqu'une loi du Journal officiel a modifié le texte.

Il s'agit d'un début, non de l'ensemble du droit congolais : d'autres codes et lois ne sont pas encore inclus, et le Code pénal et le Code de la famille n'ont pas de texte exploitable en ligne. Les lois sont hors du champ du droit d'auteur (loi n° 24-82, art. 14) ; voir `LICENSE`.
