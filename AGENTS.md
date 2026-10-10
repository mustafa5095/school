# Repository notes

Static dashboard repository. `index.html` renders every HTML file listed in
`files.json`, enriched by `description.toml`.

## Commits

All commits must be authored and committed under the repository owner's name
(`mustafa5095 <pesahngfafa@gmail.com>`). Never add co-author lines or any
mention of AI or an AI agent to commit messages.

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
