# Quest Journal: {Quest Name}

> **Place Contract** for `{quest}/journal/`
> *This README is read by journal.app as the authoritative source for this quest's journaling.*

Autobiographical memory for this quest. Insights, pivots, and friction worth preserving beyond session volatility.

---

## What This Is

The quest journal captures **narrative history** for this specific quest - not the whole project, not operational status. These are moments that shaped the quest's journey, told so anyone picking up this quest understands not just WHERE it is, but HOW it got there.

**Scope**: This quest only. For project-wide breakthroughs, see `journal/` (root).

---

## Entry Types

| Type | When to Use |
|------|-------------|
| **insight** | Understanding gained that changed approach |
| **pivot** | Significant change in quest direction |
| **friction** | Problems encountered worth documenting |
| **decision** | Choice made affecting quest outcome |
| **retrospective** | Looking back (mission complete, quest complete) |

---

## What's Journal-Worthy?

**Include** (the tactical special):
- Insights that shifted understanding mid-quest
- Pivots in approach worth explaining
- Friction that future quests might encounter
- Mission retrospectives with lasting value
- Quest completion/abandonment reflections

**Exclude** (the operational routine):
- Round status (belongs in round reports)
- Implementation details (belongs in commits)
- Working state (belongs in .mem)

**Heuristic**: *"Would someone starting a similar quest benefit from this?"*

---

## Entry Guidelines

### Structure
- **Frontmatter**: session, date, type, scope (mission or quest), tags
- **Title**: `S{###}: {Headline That Stands Alone}`
- **Sections**: The Insight, Why This Matters, References
- **Closing**: One-liner summary

### Content Qualities
- **Tactical**: Focused on this quest's concerns
- **Connective**: Link to related missions, rounds, artifacts
- **Transferable**: Wisdom that applies beyond this quest
- **Quotable**: Preserve key moments verbatim

### Length
- Shorter than project entries (quest scope is smaller)
- Sweet spot: 50-150 lines
- Longer for major pivots or quest retrospectives

---

## Entry Template

```yaml
---
session: {number}
date: {YYYY-MM-DD}
type: insight | pivot | friction | decision | retrospective
scope: {quest-name} | {quest-name}/{mission-name}
related:
  sessions: []
  artifacts: []
  entries: []
tags: []
---

# S{session}: {Headline That Stands Alone}

{Opening that captures the essence}

## The Insight

{What happened and what was learned}

## Why This Matters

{Implications for this quest or future quests}

## References

{Links to artifacts, commits, related entries}

---

*"{One-liner}"*
```

---

## Index (Chronological)

| Session | Headline | Type | Date |
|---------|----------|------|------|

---

*"The quest's story, told in moments that mattered"*
