---
name: delivery-guide
description: Writing the GUIDE document after a feature ships. Trigger when the user says a feature is shipped, finished or deployed, or asks to document what was just built. Produces a layer-by-layer record with a file inventory, bugs encountered, and remaining debt.
---

# Delivery GUIDE

You are writing what the plan could not know: **how it actually works, end to end, now that
it's built.**

## What this document is not

A guide isn't a plan written in the past tense. The plan was a **commitment** — discussed,
refused, approved. The guide is a **record**: it describes what is, including what went
wrong.

**A guide that mentions no bugs wasn't written after construction — it was written instead
of it.** If you genuinely hit no difficulty, say so explicitly rather than leaving the
section empty.

## Before writing

Reread what was actually done: the diff, the commits from the period, the original plan if
there is one. Write no line based on what was planned — only on what is in the repository
now. Here too, **measurement beats documentation**.

## The structure

Follow the path of a piece of data through the system, in flow order.

### 1. One part per layer crossed

From entry point to storage. For each: what it receives, what it does, what it returns.
**Write the interface contracts between each layer** — that's where errors lodge, and it's
the first thing anyone looks for six months later.

### 2. The data schema

Tables, columns, types, constraints, indexes. What the code assumes of the database, in
black and white. If a constraint exists in the code but not in the database, say so: that's
a pending failure.

### 3. The file inventory

Every file created or modified, with its role in one line. A thankless section, and the
most useful of all: it lets anyone find an entry point without digging through the repo.

### 4. Bugs found and fixed

What broke during construction, and why. For each: the symptom, the real cause, the fix.
This is a trap database that reads in five minutes and saves hours — the section nobody
else writes.

If a bug revealed a gap in the project's criteria grid, flag it: **that's one more
criterion to add.**

### 5. What remains

Accepted debt, untreated cases, workarounds in place. This is the starting point for the
next plan's baseline.

## Writing rules

- **Dated in the filename** (`YYYY-MM-DD-topic.md`), stored in the project's guides folder
  (`docs/guides/` by default). Two successive guides on the same system tell its evolution
  — don't overwrite the previous one.
- **Long is normal.** Several hundred to over a thousand lines for a complete system. This
  document replaces a code review by someone who wasn't there.
- **Verifiable references**: `file:line` wherever possible.
- **No flattery.** If a part is badly done, say it here rather than discovering it in a
  failure later.

## To finish

Offer the user two things:

1. adding a line to the project's memory pointing at this guide;
2. if a bug encountered was covered by no criterion, **adding that criterion to the grid** —
   that's how it grows, and the only legitimate way to grow it.
