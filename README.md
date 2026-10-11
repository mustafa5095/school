# school

If you find any mistake, either submit an issue here or message me on WhatsApp.

## Private tool

Quiz maker (not listed on the dashboard): [quiz-maker.html](https://mustafa5095.github.io/school/quiz-maker.html) — paste a quiz JSON to build a playable quiz, then download the result as a standalone HTML file with **Download Quiz**. The JSON format is in [quiz-template.json](quiz-template.json).

The builder interface is English only. The quiz it produces supports both languages on two independent axes. `meta.language` (`en`, `ku`, `both`, or `auto` when left out) sets the **interface**: the chrome, the title/subtitle/intro/author/after-test text and the explanations — `both` shows a Kurdish/English switch. `meta.content_language` (`ku` or `en`, or left out to follow the interface) sets the **test itself**: the question, answers and category. So `"language": "both"` with `"content_language": "ku"` keeps the questions and answers in Kurdish while the interface can flip to English (and vice versa). Fill the base keys for Kurdish and the `_en` keys for English. `meta.after_test` / `meta.after_test_en` add a message shown on the results screen after the quiz is finished, and `meta.author` / `meta.author_en` add an optional author line ("Quiz Author - <name>"), hidden when empty. Direction is auto-detected from each text field, so every piece of text — titles, questions, options, badges, review and the author line — renders right-to-left when it is Kurdish/Arabic and left-to-right otherwise, with no flag needed. Before downloading you can choose whether the standalone quiz includes a Home button.
