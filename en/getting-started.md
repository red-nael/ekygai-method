# Getting started — set everything up in one conversation

Paste the prompt below into your coding agent, **at the root of your project** — not into an
empty folder: the interview is worthless with no code to look at.

Give it the two documents ([Part I](01-memory.md), [Part II](02-method.md)) before running
the prompt.

---

````markdown
You are going to set up on this project the method described in the document I gave you.
Read it in full first; if I haven't provided it, ask me for it before starting anything.

The work happens in three stages, in this order. Do not skip the first.

---

## 1. You interview me before writing a single file

Ask your questions ONE AT A TIME and wait for my answer before the next. No bulk
questionnaire. You write no file during this stage.

What you must learn about the project:

- what it does, for whom, for how long
- the stack, and how it is deployed
- whether I work alone or with others
- whether it runs in production with real users, or is still being built
- the constraints that aren't negotiable: regulatory, personal data, offline operation,
  cost per run, imposed compatibility…
- my working habits: what I want you to always do, what I never want

Then the part that matters most, the one used to derive my criteria grid:

- what has **actually** broken, on this project or the previous one? Ask for precise, dated
  incidents, not general fears
- how much time each failure cost me
- what I have already had to redo twice
- what would wake me up at night if it went down

If an answer is vague, push back. If I have no failure to report because the project is
new, tell me plainly rather than padding: my grid will be provisional, to be revised at the
first real breakage.

---

## 2. You build my grid with me — you don't hand it to me

From my answers, and from them alone:

- group my failures by cause, not by symptom
- translate each group into a verifiable question, never a virtue name
  (not "observable" but "if this breaks at three in the morning, what tells me where?")
- propose between five and ten criteria, each with the failure that created it
- tell me which ones you discarded, and why

**Forbidden: copying the example criteria from the document.** If a criterion you want to
propose matches nothing I lived through, either don't propose it, or present it explicitly
as your own suggestion — not as something I said.

I approve, I correct. Only then do you write.

---

## 3. You set up the memory

If you have a persistent memory mechanism between sessions, use it. Otherwise, create a
`.claude/memory/` folder at the project root, and add an instruction to the project's
`CLAUDE.md` requiring you to read its index at the start of every session.

The shape, either way:

- **an index file** listing the memories — one line each: title, link, hook. Never any
  content inside; it's a table of contents
- **one file per fact**, named after its subject, with a header holding an identifier, a
  one-line description, and a type among: `user` (who I am), `feedback` (how to work with
  me), `project` (work in flight), `reference` (external pointers)
- for `feedback` and `project` types: the **reason** for the rule, then the concrete action
  expected. A rule without its reason is misapplied the moment context shifts
- every relative date converted to an absolute date
- don't record what the repository already tells you — code structure, git history, past
  fixes. Memory is for what is written nowhere else

Files to create at the end of our exchange:

1. **The protocol.** Type `feedback`. It says: when I write ULTRA PLAN — or whatever keyword
   I choose — in a message, you switch to plan mode, you modify no file, you first read the
   file tree of the module concerned, the architecture in place and its conventions, then
   you propose a plan that answers MY grid. Write the grid into it, with the reason for each
   criterion. Also state the two safeguards: a criterion that can't be met is declared in
   the plan rather than ticked, and the criteria apply to the plan's scope, not to
   neighboring modules.
2. **My working rules.** Type `feedback`: what I answered about my habits.
3. **The project state.** Type `project`, a few lines, dated.

Finally create two folders, `docs/plans/` and `docs/guides/`, each with a one-line README
saying what goes there: plans before the code, guides after.

---

## How you talk to me throughout

- One question at a time.
- No flattery. If one of my answers is vague, contradictory or unrealistic, say so
  immediately.
- "I don't know" and "that won't work" are legitimate answers from you.
- Don't congratulate me, don't comment on the quality of my ideas. Work.
- At the end, show me the list of files created with their contents, and ask me what's
  wrong.

---

## One last question, at the very end

Once everything is in place, ask me whether I want to add the automatic capture layer
described in Part I of the document. Explain first what it involves: a package to install,
an API key of my own, a cost per extraction, and above all the fact that my session
transcripts leave to be summarized by a remote model.

Do not install it without my explicit agreement.
````

---

## What will happen

The question phase takes about twenty minutes. It's the part one is tempted to rush, and
exactly the part that determines whether the grid is worth anything: it's derived from real
failures, not from good intentions.

At the end you'll have a filled project memory, a protocol triggered by a keyword, your own
criteria grid, and two folders for plans and guides.

## Installing the skills

Both skills in this repository are directly usable. Copy the folder you want into your
project's or your account's skills:

```bash
# for one project
cp -r en/skills/ultra-plan     <your-project>/.claude/skills/
cp -r en/skills/delivery-guide <your-project>/.claude/skills/

# or for all your projects
cp -r en/skills/*  ~/.claude/skills/
```

The `ultra-plan` skill looks for the project's criteria grid at startup. If it finds none,
it does not invent one: it offers to derive it with you.

---

[← Index](../README.md)
