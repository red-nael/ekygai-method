# GUIDE — building this repository

_Date: 2026-09-19 · Original plan: **none** (see §6)_

This guide documents the construction of the repository that publishes the method. It
serves two purposes: the usual record, and a real example of what a guide looks like — bugs
included.

## 1. The path, step by step

### Source
Two notes published as web pages in an earlier session. The original HTML files lived in a
temporary session folder, **since deleted**. Recovery was done from the published pages,
not from a local copy.

Contract to the next step: complete HTML, text plus inline SVG.

### Conversion
Text extracted by stripping tags, then rewritten as Markdown. The three SVG diagrams were
**rewritten in Mermaid**, not converted: GitHub renders Mermaid natively in light and dark
alike, whereas an SVG with fixed colors would have held in only one theme.

### Translation
The English documents are not a machine translation of the French. Fixed terms: *relevé de
cicatrices* → *record of scars*; *zéro complaisance* → *zero flattery*; *la mesure prime la
documentation* → *measurement beats documentation*; *minimum viable durable* → *durable
minimum viable*.

### Skills
Written from scratch, not derived from the documents. A document explains to a reader; a
skill gives instructions to an agent. Going from one to the other is a full rewrite, in the
imperative.

## 2. File structure

Language at the top level (`fr/`, `en/`), mirrored structure below. Alternative rejected: a
`docs/` level with language suffixes — harder to browse, and it makes the mirror invisible.

## 3. Inventory

| File | Role |
|---|---|
| `README.md` / `README.fr.md` | bilingual entry point |
| `CONTRIBUTING.md` / `.fr.md` | the criteria grid this repository applies to itself |
| `LICENSE` | MIT — skills and templates |
| `LICENSE-DOCS.md` | CC BY 4.0 — documents, with the copyright limit on a method stated |
| `{fr,en}/01-*.md` | Part I, 2 Mermaid diagrams each |
| `{fr,en}/02-*.md` | Part II, 1 diagram each |
| `{fr,en}/demarrage.md`, `getting-started.md` | the setup prompt |
| `{fr,en}/skills/*/SKILL.md` | 2 skills × 2 languages |
| `{fr,en}/{gabarits,templates}/*.md` | 4 templates × 2 languages |

## 4. Bugs found and fixed

### Backticks silently swallowed
- **Symptom**: a published sentence read "Le skill  cherche la grille" — a word missing.
- **Real cause**: an unquoted shell heredoc interpreted `` `ultra-plan` `` as command
  substitution. The shell ran `ultra-plan`, failed, and inserted an empty string.
- **Fix**: replaced by a Python script operating on the file.
- **Missing criterion?** Yes → grid criterion 3.

### Real production audit figures inside an example
- **Symptom**: the example table carried `216 rows / 48 humans`.
- **Real cause**: the example had been genericized for names, not for numbers. Since the
  repository states where the method comes from, those figures allowed a user base to be
  inferred.
- **Fix**: illustrative values. Commit `7f5a069`.
- **Missing criterion?** Yes → criterion 1.

### The capture layer installed itself into the repository
- **Symptom**: a `CLAUDE.md` and a `.memory/` appeared in the folder after the first commit,
  created by neither of us.
- **Real cause**: the automatic capture hooks described in Part I run on the machine and
  attach to any working folder — including this one.
- **Fix**: both added to `.gitignore`.
- **Missing criterion?** Yes → criterion 2. Worth noting: the failure described in Part I
  occurred on the repository that describes it.

### Diagrams and links not verifiable by reading
- **Symptom**: none — nothing broke.
- **Why it's here anyway**: Mermaid syntax (`classDef stroke-dasharray:6 4`) and the 60+
  relative links cannot be validated by eye. Verified by execution instead:
  `mermaid.parse()` in a headless browser, and resolution of every path. All 6 diagrams
  pass; the 10 links reported broken are template placeholders.
- **Missing criterion?** Yes → criterion 4.

## 5. What remains

- **The bilingual mirror has no automated check.** Nothing today prevents editing
  `fr/02-methode.md` and forgetting `en/02-method.md`. Criterion 5 exists; the tool that
  enforces it doesn't.
- **No filled-in plan example.** The templates are empty; the repository doesn't show what a
  real ULTRA PLAN looks like. Providing one would mean publishing a project's audit.
- **The repository has no memory layer of its own.** Consistent — it isn't a code project —
  but it's an accepted asymmetry, not an oversight.

## 6. What was not done, and why it's written here

**There was no ULTRA PLAN for this build.** Three framing questions, then the files were
written. No dated baseline, no phase breakdown, no grid to answer — it didn't exist yet.

Writing that plan after the fact would have produced a document dated today describing
decisions taken without it: a fabricated record, exactly what Part II forbids. So the gap is
recorded here rather than filled.

The repository's grid ([`CONTRIBUTING.md`](../../CONTRIBUTING.md)) was derived *afterwards*,
from the failures above. That's the normal order: a grid is a record of scars. Subsequent
changes will go through it.
