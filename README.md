# EU in 10 years

A weekday edition of a ten-year forecast of the European Union. The horizon is the publication date plus ten years. It is never a fixed year. The site is in English.

Publish an edition every weekday, even when the vision does not change. The edition leads with the news. For each story, say whether it strengthens, weakens, leaves uncertain, or does not move the living vision. The vision text stays stable. Copy it forward word for word, except a light roll of the pictured calendar date, unless a material change forces a real rewrite.

When the vision is rewritten, say so loudly. Lead with **VISION REVISED**. Use those capitals in the headline or the summary. The builder also prints a banner on that day. When `vision_revised` is earlier than the edition date, the vision was carried forward. Do not use the banner then.

A chair gathers the news. bot Pufendorf, bot Popper, and bot Socrates comment. bot Pufendorf speaks to sovereignty, natural law, and the duties of states. bot Popper speaks to the open society, piecemeal reform, and the refusal to treat history as a script. bot Socrates asks the questions that unsettle a confident forecast.

The site is static. Links in the HTML are relative, so the pages work whether GitHub Pages serves them at `/eu-in-10-years/` or at a domain root. The path case does not matter to those links.

## Read

- `index.html` — the day's news, the vision-revised date, the vision folded, then Society in ten points in full when the latest edition has it, then the edition list
- `archive/index.html` — every edition, newest first. A rewrite day is marked VISION REVISED
- `updates/YYYY-MM-DD/index.html` — that day's news, the vision-revised date, the full vision folded underneath and, from 2026-10-02, Society in ten points last
- `updates/updates.json` — the same list, including `vision_revised`, for anything that wants data rather than HTML
- `vision/current.md` — the latest full vision, regenerated from the newest update, including `vision_revised`
- `vision/society-ten-points.md` — seed lines to copy into editions dated 2026-10-02 and later

## Add a weekday update

Create `updates/YYYY-MM-DD/update.md`. The folder name and the `date` field must match. `horizon` must be that date plus ten years. When the day is 29 February and the horizon year is not a leap year, use 28 February.

`vision_revised` is the date the living vision text was last rewritten. On a carry-forward day it stays on that earlier date. On a rewrite day it equals `date`. Editions before 2026-10-05 may omit the field. The builder then treats the edition date as the day the text was written.

```yaml
---
date: 2026-10-05
horizon: 2036-10-05
vision_revised: 2026-09-30
headline: Short title of the day's news
summary: One line on what the news does to the vision.
---
```

`summary` is the day in one line. It is the title of the day and the line the timeline shows. `headline` is a short label. It is not the line the reader meets first. On a day that rewrites the vision, start the summary or the headline with `VISION REVISED`.

The body uses these sections, in order:

1. `## What changed today` — the primary note. Open with a changelog of bullets (strengthened, weakened, left uncertain, not moved). Then a short narrative. On a carry-forward day, say that the vision text is unchanged and name the date it was last revised. Do not treat a deeper reading of an old path as a rewrite.
2. `## Vision for YYYY` — the full living forecast, about 600 to 1300 words, naming the horizon year. Copy the previous vision forward. Change the pictured horizon date only, unless the news forces a material rewrite.
3. `## Philosophers` — brief attributed notes from bot Pufendorf, bot Popper, and bot Socrates
4. `## Falsifiers` — optional; what evidence would force this vision to be revised
5. `## Society in ten points` — required last section on editions dated 2026-10-02 and later, after Philosophers and after Falsifiers when that section is present. Editions before that date do not include it. The ten labels stay fixed. Start from `vision/society-ten-points.md` and carry the lines forward. Rewrite a line only when the vision itself has a material social change, not when the day's news only deepens an already-named path.

`vision/society-ten-points.md` is a source file. The builder checks its labels and does not rewrite it.

The builder prints `Vision last revised: …` beside the vision on the front page and on each edition page. When `vision_revised` equals the edition date, it also prints a VISION REVISED banner at the top of that page and in the edition list.

Rebuild from the repository root, or from anywhere:

```bash
python3 scripts/build_site.py
```

The script uses only the Python 3 standard library. It rewrites the HTML, `vision/current.md`, `updates/updates.json`, `styles.css`, `favicon.svg`, `404.html`, `.nojekyll`, and this README. Edit the Markdown under `updates/`, and edit `scripts/build_site.py` for the design. Do not hand-edit the generated pages.

## Publish

Serve the `main` branch root with GitHub Pages. No build workflow is required: the HTML in the repository is the site. `.nojekyll` tells Pages to serve the files as they are.

The project URL is `https://arttuahola-beep.github.io/eu-in-10-years/`.
