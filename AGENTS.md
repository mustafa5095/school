# Repository notes

Static dashboard repository. `index.html` renders every HTML file listed in
`files.json`, enriched by `description.toml`.

## Commits

All commits must be authored and committed under the repository owner's own
name and email. Auto-detect the identity from the existing git history
(`git log --format='%an <%ae>'`, which yields the prior commits' author) and
configure it with `git config user.name` / `git config user.email` before
committing. Never add co-author lines or any mention of AI or an AI agent to
commit messages, and never hardcode or expose the owner's email anywhere in the
repository.

## New pages

`template.html` is the site's style/layout template (Tailwind CDN, Vazirmatn
font, slate/emerald palette, RTL, DOM-built UI, Kurdish digits) — not a
quiz-specific template. Copy it to start any new page, then register that page
in `files.json` and `description.toml`. Do not list `template.html` itself as a
page.

Every page must include the author credit footer
(`دروستکەر: مصطفی زەردەشت` / `Created by Mustafa Zardasht`).

## File metadata (`description.toml`)

One section per file: `["<filename>.html"]` with keys:

- `title` / `title_en`
- `description` / `description_en`
- `category` (Kurdish/default) / `category_en` (English)

`category` values are virtual UI paths, not real directories. `"Quizes/Week1"`
creates a `Quizes` folder containing a `Week1` subfolder in the webpage.

## Quiz maker

`quiz-maker.html` builds a playable quiz from pasted JSON (see
`quiz-template.json` for the schema, meant to be handed to an AI). It replicates
the engine of `quiz-2nd-arabicreligion.html`: shuffled questions per category,
shuffled options, progress bar, per-category scores, review with explanations,
keyboard navigation and Kurdish digits.

`meta.interface` picks the interface language: `"ku"` (Kurdish only, no switch),
`"en"` (English only), or `"both"` (language switch shown). Content is bilingual:
each text field has a Kurdish base key and an English `_en` key, and the other
language falls back automatically when one is missing.

## Category descriptions

Categories can be described in `description.toml` with
`[categories."<Path>"]` sections, where `<Path>` is the slash path (usually
the English spelling). Supported keys: `name`, `name_en`, `description`,
`description_en`. The dashboard matches these sections against either
language's category spelling, so it works while viewing Kurdish or English.
