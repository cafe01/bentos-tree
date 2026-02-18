---
name: journal
description: Autobiographical memory for any Place. Create and curate journal entries that capture moments worth preserving. Invoke with optional PLACE argument to journal at specific locations (e.g., /journal c01/q01).
argument-hint: [PLACE]
belf:
  text:
    - app_abstract.xml
    - app_concrete.xml
---

# Journal App

Autobiographical memory substrate - the tool for journaling at any Place.

> *"The journal is how memory becomes meaning."*

## Invocation

```
/journal [PLACE]
```

**PLACE resolution:**

| Invocation | Resolves To |
|------------|-------------|
| `/journal` | `journal/` (root) |
| `/journal c01/q01` | `campaigns/c01-*/q01-*/journal/` |
| `/journal c02/q04/m03` | `campaigns/c02-*/q04-*/m03-*/journal/` |
| `/journal books/agent-harness` | `books/agent-harness/journal/` |

**Quest-forge shorthand:**
- `c##` expands to `campaigns/c##-*/`
- `c##/q##` expands to `campaigns/c##-*/q##-*/`
- `c##/q##/m##` expands to `campaigns/c##-*/q##-*/m##-*/`

## The Pattern

Journal.app is the **tool for journaling**. Places have journals.

Like a carpenter (tool) working in different workshops (places):
- Project journal lives at `journal/`
- Quest journals live at `campaigns/.../journal/`
- Any Place can have a `journal/` subdirectory

**Journal.app knows journaling. Places know their context.**

Types, schemas, frontmatter are context-specific. Journal.app provides the essence: autobiographical memory - who have I been, what is my story.

---

*Scope-agnostic memory keeping - for any entity that wants to remember who it has been*
