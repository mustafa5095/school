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

`template.html` is a full starter page in the repository's style (Tailwind CDN,
Vazirmatn font, slate/emerald palette, RTL, DOM-built UI, Kurdish digits). Copy
it to create a new page, then register that page in `files.json` and
`description.toml`. Do not list `template.html` itself as a page.

Every page must include the author credit footer
(`دروستکەر: مستەفا زەردەشت` / `Created by Mustafa Zardasht`).

## File metadata (`description.toml`)

One section per file: `["<filename>.html"]` with keys:

- `title` / `title_en`
- `description` / `description_en`
- `category` (Kurdish/default) / `category_en` (English)

`category` values are virtual UI paths, not real directories. `"Quizes/Week1"`
creates a `Quizes` folder containing a `Week1` subfolder in the webpage.

## Category descriptions

Categories can be described in `description.toml` with
`[categories."<Path>"]` sections, where `<Path>` is the slash path (usually
the English spelling). Supported keys: `name`, `name_en`, `description`,
`description_en`. The dashboard matches these sections against either
language's category spelling, so it works while viewing Kurdish or English.
