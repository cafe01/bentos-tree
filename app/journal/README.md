# Journal

**FQDN:** `journal.app`
**Kind:** Living Application
**Version:** 1.0

---

## What It Is

Autobiographical memory for any Place. Journal transforms experience into meaning — preserving the moments worth remembering beyond operational volatility.

Not an activity log. Not a status report. A **narrative record** of who you've been and what you've learned. Marcus Aurelius, not Jira.

## How It Works

Journal is scope-agnostic. It knows journaling — narrative craft, curation, the Meditations Principle. Places define their own journaling context through a lightweight contract (`{place}/journal/README.md`).

Any place can have a journal. The place's contract says what's worth recording there. Journal provides the craft of recording it well.

## The Meditations Principle

Headlines are wisdom, not timestamps. "The impediment to action advances action" teaches across centuries. "Day 47: Had thoughts about Stoicism" does not.

When sessions scroll into history, only headlines remain. They must be self-sufficient.

## Curation

**Include:** shifts in understanding, decisions that echo, patterns that apply broadly, pivots, insights that die with context.

**Exclude:** implementation details (commits), status (operational memory), task tracking (PM tools), specs (docs).

**Heuristic:** "Would a future collaborator benefit from knowing this happened?"

## Organism-Aware

Journal owns autobiographical memory — one specific type in the broader system. The organism's anamnesis faculty manages the rest (episodic, semantic, prospective). Journal doesn't duplicate that taxonomy. Obsidian-compatible markdown is handled by the required obsidian.markdown.tools.skill.

## Package

```
app/journal/
  atom.xml    # Monolithic (abstract + concrete)
  README.md   # This file
```

## Install

```
bentos-agent pkg install journal.app
```
