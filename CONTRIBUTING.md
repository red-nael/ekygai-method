# Contributing — and the grid this repository applies to itself

English · [Français](CONTRIBUTING.fr.md)

This repository describes a method. It would be dishonest to publish it without applying it
here. So this file holds **the criteria grid for this repository itself**, derived the way
the method prescribes: from what has actually broken, not from good intentions.

Every criterion below was born of a real failure during construction, dated. None was
invented to look complete.

## The grid

| # | Criterion | Born of |
|---|---|---|
| 1 | **Nothing here lets anyone infer the activity or scale of the projects the method came from.** Figures in examples are illustrative and must not be real. | 2026-09-19 — the audit example table shipped with the real numbers of a production audit (`216 rows / 48 humans`). Caught before the first push. |
| 2 | **Nothing a machine generates on its own enters the repository without a decision.** | 2026-09-19 — the automatic capture layer created a `CLAUDE.md` and a `.memory/` in this very folder during the writing session. A distracted `git add -A` would have pushed session memories to a public repo. |
| 3 | **Every file written is reread as it sits on disk, not as it was meant to be written.** | 2026-09-19 — a shell heredoc interpreted backticks as command substitution and silently deleted a word from a published page. Found by grep, not by rereading the source. |
| 4 | **Everything that renders — diagrams, links — is verified by execution, never by reading.** | 2026-09-19 — the Mermaid diagrams were validated by parsing them in a headless browser; the internal links by resolving each path. Neither would have been caught by proofreading. |
| 5 | **Any change to a document has its mirror in the other language, in the same commit.** | Structural: a bilingual repository drifts silently. The French and English versions are not translations of each other, they are two faces of the same document. |

## The two safeguards

A criterion that cannot be met is **declared in the pull request**, with its reason. A pull
request that ticks all five out of politeness is worth nothing — the value is in the
admission.

The criteria apply **to the scope of the change**, not beyond. Fixing a typo does not
require auditing the whole repository.

## What a useful contribution looks like

Field reports first: **which criteria grid did your project produce, and which failure
created it?** That is the only part of this method that cannot be written in advance, and
the part most worth collecting.

Translations, corrections and clarifications are welcome. Ready-made criteria grids are
not: publishing one would contradict the method.

## Trace

The guide of this repository's own construction, including the bugs above, is in
[`docs/guides/`](docs/guides/). There is no plan document for the initial build — it was
written without one, and writing one after the fact would be exactly the fabricated record
this method forbids.
