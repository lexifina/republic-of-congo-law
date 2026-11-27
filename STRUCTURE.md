# Structure

Le dépôt range chaque texte par nature puis par année, sous des noms en français.

| Dossier | Contenu |
| --- | --- |
| `constitution/` | La Constitution du 25 octobre 2015 (préambule et articles), avec ses modifications |
| `codes/<code>/` | Les codes (`codes/code-penal/`) |
| `lois/<année>/<numéro>-<objet>/` | Les lois et lois organiques |
| `ordonnances/<année>/<numéro>-<objet>/` | Les ordonnances |
| `decrets/<année>/<numéro>-<objet>/` | Les décrets |
| `arretes/<année>/<numéro>-<objet>/` | Les arrêtés (les numéros recommencent chaque année et par ministère) |

Dans chaque dossier de texte : `README.md` (titre, source, date, couche texte), `visas.md`, un fichier par article
(`art-001.md` pour l'article premier, `art-012-bis.md`), `signatures.md`, ou `texte-integral.md` quand aucun article
n'est repéré. Aucun dossier ne compte plus de 1 000 entrées.

`corpus.json` liste les textes (`cg/national/acts`) ; `data/` et `tools/` datent de la première construction
(Journal officiel, octobre 2026).

## Structure (English)

Each act is filed by type, then year, under French names: `constitution/`, `codes/<code>/`,
`lois/<year>/<number>-<object>/`, `ordonnances/`, `decrets/`, `arretes/` (arrêté numbers restart each year and per
ministry). In each act folder: `README.md`, `visas.md`, one file per article, `signatures.md`, or `texte-integral.md`
when no article was found. No folder holds more than 1,000 entries.
