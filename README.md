# The EKYGAI Method

English · **[Français](README.fr.md)**

> A way of working with a coding agent: a memory that survives the end of a session, and a
> protocol that forbids writing code before reading what already exists.

Refined over several years of real development, first on [EKYGAI](https://ekygai.com). This
repository publishes the method only — never the product.

---

## The problem

A coding agent understands an architecture after two hours of conversation, then the
session ends and it all goes. And if nothing is imposed on it, it starts writing as soon as
it believes it has understood — which happens very fast. The result compiles, looks right,
ignores half the repository's conventions. It survives the sprint. It breaks by the
quarter.

Two answers, neither of which holds without the other.

## The two parts

| | |
|---|---|
| **[Part I — Two Layers of Memory](en/01-memory.md)** | Automatic capture through hooks, plus an index written by hand. Where facts live, what makes them decay, what it costs — including what it sends off your machine. |
| **[Part II — Before the Code, After the Code](en/02-method.md)** | The `ULTRA PLAN` protocol before writing, the `GUIDE` document after shipping. And the criteria grid everyone must build for themselves. |

## What's in the repository

```
en/
├── 01-memory.md           the two memory layers, with diagrams
├── 02-method.md           the protocol and the two documents
├── getting-started.md     the prompt that sets everything up in one conversation
├── skills/
│   ├── ultra-plan/        planning protocol, executable
│   └── delivery-guide/    writing the guide after shipping
└── templates/             memory index, fact sheet, plan, guide
```

`fr/` mirrors the same content in French.

```
CONTRIBUTING.md            the criteria grid this repository applies to itself
docs/guides/               including the guide of this repository's own construction
docs/plans/                empty — see that guide, §6
```

**This repository applies its own method.** Its grid is in
[`CONTRIBUTING.md`](CONTRIBUTING.md), derived from four failures that happened while
building it. The guide of that build —
[`docs/guides/2026-09-19-repository-build.md`](docs/guides/2026-09-19-repository-build.md) —
records them, including the one the method itself warns about: the automatic capture layer
silently installed itself into this folder.

## Installation

Nothing to install for the essential layer. Copy the skills, give the two documents to your
agent, then run the prompt in [`en/getting-started.md`](en/getting-started.md).

```bash
git clone https://github.com/red-nael/ekygai-method.git
cp -r ekygai-method/en/skills/* ~/.claude/skills/
```

The `ultra-plan` skill looks for your project's criteria grid. If it finds none, **it does
not invent one**: it offers to derive it with you, from the failures you have actually
lived through.

## What this repository is not

- **Not a tool.** No service to run, no mandatory dependency.
- **Not a ready-made criteria grid.** It was deliberately removed: a criterion you never
  paid for is never defended, it is ticked. The method explains how to derive your own in
  five steps.
- **Not a guarantee.** The method guarantees a level of result, not the result. It prevents
  work from being sloppy; it doesn't decide what to build.

## Licenses

| What it is | License |
|---|---|
| Documents (`en/*.md`, `fr/*.md`) | [CC BY 4.0](LICENSE-DOCS.md) — free reuse, including commercial, **with attribution** |
| Skills and templates | [MIT](LICENSE) — copy, modify, adapt: that's what they're for |

A working method isn't protectable by copyright — only its expression is. These licenses
govern reproduction of the text, not use of the ideas.

## Author

**Redouane El Bakkouch** — [EKYGAI](https://ekygai.com)

Contributions welcome — see [`CONTRIBUTING.md`](CONTRIBUTING.md). Field reports first:
which criteria grid did your project produce, and which failure created it.
