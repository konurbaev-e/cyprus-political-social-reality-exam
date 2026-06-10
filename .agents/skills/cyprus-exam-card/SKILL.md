---
name: cyprus-exam-card
description: Create Markdown study-card files for the Cyprus political/social reality exam from user-provided Greek/Russian question data. Use when the user asks to create a file/card "по аналогии с текущими файлами в проекте", provides a correct answer, Greek title, Russian title, question, answer options, translations, word-by-word analysis, grammar notes, or asks to convert exam-question material into the repository's .md card format.
---

# Cyprus Exam Card

## Workflow

1. Inspect the current repository before writing if the format is uncertain. Read 1-2 existing `.md` cards and follow their structure over any generic Markdown preference.
2. Extract from the user message: Greek title, Russian title, Greek question, Russian question translation, answer options, correct answer, vocabulary/grammar explanations, features, and exam context.
3. Create one new `.md` file in the current project root unless the user specifies another directory.
4. Name the file with the Greek title and Russian title in lowercase, joined by hyphens:
   `греческий-заголовок-русский-заголовок.md`
5. Use `apply_patch` for file creation or edits.
6. After writing, read the file back with UTF-8 and run `git status --short`.
7. Add the created or modified task file(s) to Git tracking with `git add -- <path>`. Do not create a commit unless the user explicitly asks for one.
8. In the final response, link the created file and mention the marked correct answer. Do not summarize every vocabulary item.

## Card Format

Use this layout unless existing project files clearly show a newer pattern:

```markdown
# Greek Title - Русский заголовок

Greek question?
> Русский перевод вопроса?

- word — начальная форма: ...; translation/explanation.
- word — ...

Особенности:
Short grammar/usage notes.

---

- Wrong option
> Translation.

- Correct option - ✅ ВЕРНО
> Translation.

---

- Option vocabulary item — начальная форма: ...; explanation.

---

Правильный ответ:
`Correct option`

Контекст для экзамена:
Why this answer is correct.
```

## Content Rules

- Preserve the user's Greek wording for the question and options unless correcting an obvious typo is necessary; mention meaningful corrections in the card note or final response.
- Keep vocabulary in order of appearance.
- Include all provided important words; do not split nouns and verbs into separate sections.
- For nouns, include article and gender when available: `η υπηρεσία; ж.р.`
- For verbs, include infinitive/lemma plus `Υποτακτική`, `Παρατατικός`, and `Αόριστος` when the user provides or expects them.
- Use short Russian translations directly under each Greek question/option with blockquote `>`.
- Mark exactly one correct option with `- ✅ ВЕРНО` unless the user explicitly says the question has multiple correct answers.
- Use backticks for key Greek phrases in notes and for the final correct answer.
- Keep the card concise enough to match the repository style; remove duplicated prose from the user's raw input.

## Fact Checking

- If the fact is historical and stable, use the user's supplied correctness unless it conflicts with known project context.
- If the fact is current, future-dated, political, legal, financial, regulatory, or otherwise likely to change, verify it with an official or primary source before writing.
- If verified data differs from the user's wording, preserve the test wording in the question but add a concise clarification in `Контекст для экзамена`.
- Cite sources in the card only when verification materially affects the answer or date.

## Filename Rules

- Prefer the Greek title first, then Russian title.
- Lowercase Latin/Cyrillic/Greek letters where natural.
- Replace spaces and punctuation with single hyphens.
- Keep Greek accents.
- Keep established short Latin names as-is when part of a proper noun, e.g. `great-sea-interconnector`, `eurogroup`.
- Avoid trailing hyphens.

## Communication

- Before writing, briefly state that a card will be created using the project format.
- If browsing is needed for fact checking, say what is being verified.
- If `rg` is unavailable, use PowerShell alternatives without treating it as a blocker.
- Final response should be brief: created file link, verification status if relevant, and any untouched unrelated git changes such as `.idea/`.
