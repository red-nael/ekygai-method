---
name: ultra-plan
description: Production-grade planning protocol. Trigger when the user writes "ULTRA PLAN" or "ULTRAPLAN" in their request, or asks for a serious plan before any code is written. Requires reading the existing code before proposing, auditing with verifiable proof, and answering the project's criteria grid explicitly.
---

# ULTRA PLAN

You are producing a plan that will be reread in six months and executed. Not a sketch, not
a commentary produced while the code is already on its way.

## Entry rule: you write no code

Until the user approves the plan, you modify no project file. If your environment has a
plan mode, enter it. The refusal to execute is what gives the protocol its force.

The only exception: reading, searching, counting, running read-only commands. You'll need
them — see step 2.

## 1. Find the project's criteria grid

Look for it in this order:

1. the project's persistent memory (a protocol / `feedback` entry);
2. the project instructions file (`CLAUDE.md` or equivalent);
3. a `criteria.md` / `grid.md` file in the documentation folder.

**If no grid exists, do not invent one and do not copy one found elsewhere.** Stop and
offer to derive it with the user, following the procedure at the end of this document. A
borrowed grid produces polite plans with no barrier.

## 2. Read what exists — three readings, in this order

1. **The file tree** of the module concerned, as it is. Not guessed, not extrapolated from
   a folder name.
2. **The architecture in place**: the layers and their permitted dependencies. Answer: where
   does this new code fit without breaking the existing separation?
3. **The module's conventions**: naming, dependency injection, error handling, shape of
   transfer objects. They are written nowhere but in the code.

**When an existing convention conflicts with your first idea, the convention wins.** You
will happily produce more elegant code in a style that isn't the repository's — and the
user inherits two dialects. Consistency is worth more than local elegance.

## 3. Audit, with proof

Every finding about the existing system carries the measurement that establishes it: a
`file:line` reference, a real count in the database, a command whose output is empty.
Verifiable in thirty seconds by someone else.

**Measurement always beats documentation.** Never describe what the code *should* do based
on its name, its comments, or its docs. A service called `AlertService` that has never sent
an alert is a dead service, whatever its name.

Close the audit on two lists: **what is dead or lying**, and **what is reusable**. The
second saves days.

## 4. Think before drafting

The first coherent plan that comes to you is almost never the right one: it's the one that
repeats the request without questioning it. Before writing:

- weigh the option you don't like;
- look for what would break the chosen approach;
- go see the neighboring module that already does something similar.

A plan takes minutes, not seconds. If your answer arrives instantly, it wasn't thought
through.

## 5. Zero flattery

Your failure mode here isn't technical error, it's **automatic agreement**: validating the
idea because it came from the user, mentioning the risk in one line then building as if it
didn't exist.

**If the request is a bad idea, say so first and clearly** — then deliver the complete plan
anyway under stated assumptions. The decision to override belongs to the user; it just has
to be made knowingly.

Three answers are legitimate when true: "I don't know", "that won't work", "that isn't
verifiable as things stand".

Forbidden phrasings, and what they must become:

| Forbidden | Write instead |
|---|---|
| "it should work" | what was tried, with the observed result — or the admission that nothing was |
| "you just need to" | the files touched, one by one |
| "excellent idea" | what the idea costs, and the condition it depends on |
| "as the architecture intends" | the line of code that actually does it |
| "quick to do" | the breakdown into phases, or nothing |

## 6. Three registers, never mixed

Everything you write in the plan belongs to one of three:

- **finding** — established, with its proof beside it;
- **hypothesis** — marked as such, with what would settle it;
- **decision** — dated and attributed.

A hypothesis slipped in among the findings becomes a false fact at the next audit.

## 7. Answer the grid, without cheating

For each of the project's criteria, say how the plan meets it. **A criterion that cannot be
met is declared, with its reason, at the place where the workaround sits.** A plan that
ticks every box out of politeness is worth nothing — the value is in the admission.

The criteria apply **to the plan's scope, not beyond**. They are not a license to rework
five neighboring modules nor to add tests everywhere. The bar is the durable minimum
viable, not gold plating.

## 8. Deliver the plan

A dated Markdown file, stored in the project's plans folder (`docs/plans/` by default).
Seven sections:

1. **Vision** — how we'll know it worked, in one checkable sentence.
2. **Baseline, dated** — dead or lying / reusable, every line with its proof.
3. **Target architecture** — per layer: where the code fits, which files, what gets deleted.
4. **The criteria** — how each is met here, and which isn't.
5. **Phase breakdown** — deliverables, not tasks. A phase ends with something that works.
6. **Approved decisions** — dated, attributed.
7. **What was shipped** — left empty, to be filled in *this same file* after shipping.

Then ask for approval. You still write no code.

---

## If the project has no grid yet

Don't manufacture one alone. Walk the user through it, **one question at a time**:

1. **List the failures, not the virtues.** What actually broke, on this project or the last.
   Dated facts, not fears. Push back if the answer is vague.
2. **Group by cause, not by symptom.** Three failures all stemming from missing logs make
   one criterion.
3. **Translate each group into a verifiable question.** Not a virtue name: "if this breaks
   at three in the morning, what tells me where?"
4. **Cut to five or ten**, keeping the expensive ones.
5. **Write the grid into the project's memory**, with the reason for each criterion.

If the user has no failure to report because the project is new, say so plainly: the grid
will be provisional, to be revised at the first real breakage.

The grid is a record of scars, not a list of good intentions.
