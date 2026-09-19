---
name: identifier-in-kebab-case
description: One line that lets relevance be judged at recall time.
type: user | feedback | project | reference
---

One file = one fact. The filename repeats the `name` field.

**The four types:**

- `user` — who I am: role, expertise, lasting preferences
- `feedback` — how to work with me: corrections given, approaches confirmed
- `project` — work in flight, goals, constraints not derivable from the code
- `reference` — external pointers: URLs, dashboards, tickets

For `feedback` and `project`, add these two lines:

**Why:** the reason behind the rule — without it, the rule is misapplied the moment context
changes.

**How to apply:** the concrete action expected next time.

Links to other memories: `[[name-of-other-memory]]`. A link to a memory that doesn't exist
yet is fine — it marks what still needs writing.

Every relative date is converted to an absolute date at write time.

Don't record what the repository already tells you: code structure, git history, past
fixes. Memory is for what is written nowhere else.
