---
name: tools.markdown.obsidian
description: Obsidian-compatible markdown patterns - works everywhere, enhanced in Obsidian.
user-invocable: false
belf:
  text:
    - skill_abstract.xml
    - skill_concrete.xml
---

# Obsidian-Compatible Markdown

Portable markdown patterns that work everywhere, enhanced when viewed in Obsidian.

> *"Works everywhere. Enhanced in Obsidian."*

## Core Principle

Standard markdown is the universal language. Obsidian adds enhancements (graph, backlinks, Dataview) but the documents themselves should remain portable.

## The Tradeoff Resolved

```
Wikilinks: Beautiful in Obsidian, broken everywhere else
Standard links: Work everywhere, still clickable in Obsidian

-> Standard links win. Portability is not optional.
```

## Frontmatter Categories

| Category | Obsidian Behavior | Examples |
|----------|------------------|----------|
| **Indexed** | Native search, tags pane | `tags:`, `aliases:`, `cssclasses:` |
| **App-specific** | Dataview queryable only | `status:`, `version:`, any custom |

---

*TOOLS axis: what we use*
