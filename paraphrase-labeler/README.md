# Paraphrase labelling — for annotators

You are judging whether a rewritten question still asks the same thing as the
original. Three verdicts:

| verdict | when |
|---|---|
| **same** | the rewrite means the same thing; a person who knew the answer to the original would give the same answer |
| **different** | the rewrite asks for something else — a different quantity, a different entity, a narrower or wider scope, a changed condition |
| **invalid question** | the rewrite is broken rather than merely changed: ungrammatical, truncated, no longer a question, or it states an answer instead of asking |

`different` and `invalid question` are kept apart on purpose. The first means
the paraphraser silently changed the task; the second means it produced text
that is not a usable question at all. They are different bugs.

## Running it

**Simplest — no install.** Double-click `label_paraphrases.html`. It opens in
your browser. Click *"Sheet won't load? Paste the CSV or pick a file instead"*
and load the CSV you were sent with the file picker.

**Only if you need to load a Google Sheets link:** double-click
`start_labeler.command` (macOS/Linux) or `start_labeler.bat` (Windows), which
serves the folder over `http://` and opens the page. Leave that window open
while you work. Browsers block a `file://` page from fetching a Google Sheet,
which is the one thing the launcher exists to fix.

A Google Sheet also has to be **published to the web** to be readable this way:
in Sheets, *File → Share → Publish to web → Comma-separated values*. A normal
"anyone with the link" share will not work.

## Labelling

- Keyboard is much faster than the mouse: <kbd>1</kbd> same, <kbd>2</kbd>
  different, <kbd>3</kbd> invalid question. Each one labels and advances.
- <kbd>&larr;</kbd> <kbd>&rarr;</kbd> move without labelling, <kbd>u</kbd>
  jumps to the next unlabelled row, <kbd>f</kbd> toggles the full text.
- Long questions collapse the unchanged parts to a `N unchanged words` chip, so
  a one-word edit inside a long passage is visible. Click the chip or press
  <kbd>f</kbd> to read the whole thing — worth doing whenever the verdict is
  not obvious, because context can change what an edit means.
- **From row / To row** limits you to a slice, so two people can split the set.
- Use the **Note** field when a row is genuinely arguable. Those are the
  interesting ones.

## Sending labels back

Your work autosaves in your own browser as you go, but that is not a backup —
export before you finish a session:

- **Download CSV** gives `row_id, dataset, same_meaning, notes`. Send that file.
- **Copy for Sheets** puts the same rows on your clipboard, tab-separated, to
  paste straight into a shared sheet.

Labels are stored per-browser, so if two of you label the same rows
independently, that is deliberate — the disagreements measure how much of this
judgement is genuinely contested.
