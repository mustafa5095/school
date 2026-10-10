# Repository notes

Static dashboard repository. `index.html` renders every HTML file listed in
`files.json`, enriched by `description.toml`.

## Testing before you push

Never claim something works without testing it. Every change must be exercised
in a real browser before committing, and every feature touched must be verified
individually. Do not push a change that has not been run.

Test rules:

- Drive the real page in a headless browser (Chromium is installed; Puppeteer
  Core can be installed temporarily under `/tmp`). Do not rely on reading the
  code or on a partially-simulated harness.
- Fail the run on any uncaught page error, `console.error`, or unexpected HTTP
  4xx/5xx. The only acceptable console noise is the `favicon.ico` 404 (this repo
  ships no favicon).
- Exercise every affected feature end to end and assert on the rendered DOM, not
  on internal variables. For the quiz maker that means: build, start, answer,
  finish, review, switch language at every screen, restart, download, open the
  downloaded file and play it, and the negative paths (bad JSON, empty
  questions).
- Both languages must be checked wherever text can appear: page content, all
  buttons/labels, category badges, counters, scores and the review. Confirm the
  direction switches and that Kurdish uses Kurdish digits.
- Test both languages of the input too: a bilingual quiz and a single-language
  quiz, since the language switch must only appear for the bilingual one.
- Clean up any temporary test files you create; never leave them in the served
  directory.
- Only after all checks pass, commit and push.

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

`quiz-maker.html` is a private tool (linked from `README.md`, not listed in
`files.json`, so it never shows on the dashboard). Its builder interface is
English only, but the quiz it produces is bilingual, and it replicates the
engine of `quiz-2nd-arabicreligion.html`: shuffled questions per category,
shuffled options, progress bar, per-category scores, review with explanations
and keyboard navigation.

Quiz content may be Kurdish, English, or both: each text field has a base key
(Kurdish) and an English `_en` key. When both are present the quiz shows a
Kurdish/English switch and follows the quiz's language for both content and
chrome; when only one is present the quiz stays in that language.

The page can download the built quiz as a standalone HTML file (JSON embedded,
no dependency on the maker), with an option to include a Home button that links
to `index.html`.

## Category descriptions

Categories can be described in `description.toml` with
`[categories."<Path>"]` sections, where `<Path>` is the slash path (usually
the English spelling). Supported keys: `name`, `name_en`, `description`,
`description_en`. The dashboard matches these sections against either
language's category spelling, so it works while viewing Kurdish or English.
