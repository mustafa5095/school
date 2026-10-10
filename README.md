# school

If you find any mistake, either submit an issue here or message me on WhatsApp.

## Private tool

Quiz maker (not listed on the dashboard): [quiz-maker.html](quiz-maker.html) — paste a quiz JSON to build a playable quiz, then download the result as a standalone HTML file with **Download Quiz**. The JSON format is in [quiz-template.json](quiz-template.json).

The builder interface is English only. The quiz it produces supports both languages: fill the base keys for Kurdish and the `_en` keys for English, and set `meta.language` to `en`, `ku` or `both` to force a single language or a Kurdish/English switch. Leave it out (or set `auto`) and the quiz uses whichever languages the content provides. `meta.after_test` / `meta.after_test_en` add a message shown on the results screen after the quiz is finished, and `meta.author` / `meta.author_en` add an optional author line ("Quiz Author - <name>"), hidden when empty. Direction is auto-detected from each text field, so every piece of text — titles, questions, options, badges, review and the author line — renders right-to-left when it is Kurdish/Arabic and left-to-right otherwise, with no flag needed. Before downloading you can choose whether the standalone quiz includes a Home button.
