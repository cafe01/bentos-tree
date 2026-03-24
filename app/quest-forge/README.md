# QuestForge

**FQDN:** `quest-forge.app`
**Kind:** App (LApp)
**Status:** v7 — monolithic atom, redesigned hierarchy

---

## What It Is

QuestForge is a quest-driven project management framework for BentOS agents. It structures work as a fractal hierarchy of campaigns, quests, and missions — providing operational coherence without bureaucratic overhead.

It is NOT a visual PM tool, a chatbot wrapper, or a gamified to-do list. It is a **warroom discipline** — a way for agents (and the humans who work with them) to coordinate complex, multi-front endeavors through structured hierarchy and progressive discovery.

## The Hierarchy

Four fractal levels, each self-similar:

| Level | Scope | Artifact | Contains |
|-------|-------|----------|----------|
| **Warroom** | The endeavor | `hq/warroom/README.md` | Campaigns |
| **Campaign** (`c##-name/`) | Strategic initiative | `README.md` + quest matrix | Quests |
| **Quest** (`q##-name/`) | Deliverable goal | `README.md` + mission matrix | Missions |
| **Mission** (`m##-name.md`) | Tactical execution | Self-contained file | (leaf) |

Warroom README defines the telos — the single coherent endeavor the entire hierarchy serves. Every campaign, quest, and mission traces back to it.

## Design Principles

**Exploration over planning.** Lift fog progressively. Each completed mission reveals what's next. Don't plan what fog hasn't revealed.

**Intel flows.** Strategy flows DOWN (warroom to mission). Wisdom flows UP (mission to warroom). Each level has perfect briefing — no more, no less.

**Compartmentalization.** Each level sees only what it needs. A mission doesn't know about sibling missions. A quest doesn't know about sibling quests. Reduces cognitive load, prevents scope bleed.

**Lean coordination, not artifact factory.** The warroom is mission control, not a filing cabinet. `ls` a quest directory and you see exactly what's live. More than a handful of files = red flag.

**Work happens at target locations.** Missions point to where work actually lives (the codebase, a package, a business doc). The warroom tracks and coordinates — it doesn't contain deliverables.

## Mission Lifecycle

Missions are files, not directories. A mission file (`m##-name.md`) is self-contained: definition, success criteria, progress, accumulated knowledge, deliverable pointers.

**States:** BLOCKED | REVEALED | ACTIVE | COMPLETE | ABANDONED

**Completion = debrief + delete.** When a mission completes:
1. Extract intel into the quest's mission matrix (one row: number, name, goal, status, outcome)
2. Delete the mission file
3. Git preserves the full history if ever needed

No archive directories. No stale artifacts. The mission matrix in the quest README is the institutional memory.

## Quest README Structure

The quest README is the authority for its scope:

- **Quest definition** — what, why, scope boundaries
- **Mission Matrix** — all missions ever (active and completed), one row each
- **Active landscape** — current state, blockers, priorities

Same pattern repeats at campaign level (quest matrix) and warroom level (campaign matrix).

## Modes

QuestForge operates in two modes:

**Master (orchestrator):** Coordinates from main context. Designs missions, reviews outcomes, propagates intel. Never explores or codes directly — spawns workers for that.

**Worker (executor):** Operates inside spawned task contexts. Receives mission context + tactical scope. Executes autonomously, reports back via structured outcomes. Fresh mind + proper loadout = better positioned than orchestrator to decide HOW.

## Intel Classification

| Classification | Scope | Flow |
|---------------|-------|------|
| TACTICAL | Stays at mission | Captured in mission file |
| OPERATIONAL | Bubbles to quest | Captured in quest README |
| STRATEGIC | Bubbles to campaign | Captured in campaign README |
| DOCTRINAL | Bubbles to warroom | Captured in warroom README |

## What QuestForge Is Not

- Not a visual UI (though one could be built on top)
- Not session-scoped (sessions are temporal; quests are goal-scoped)
- Not prescriptive about tools or languages
- Not BentOS-specific — any agent with filesystem access can run a warroom

## Package Contents

```
app/quest-forge/
  atom.xml              # Monolithic package (abstract + concrete)
  README.md             # This file
```

## Install

```
bentos-agent forge install quest-forge.app
```
