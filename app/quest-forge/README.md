# QuestForge

**FQDN:** `quest-forge.app`
**Kind:** Living Application
**Version:** 9.0

---

## What It Is

RPG-inspired project management. QuestForge turns complex work into adventure through a fractal hierarchy of campaigns, quests, and missions — with fog-of-war mechanics, narrative engagement, and structured intel flow.

Not a gamified to-do list. A **warroom discipline** that makes the everyday grind feel like progress in an adventure. The RPG vocabulary isn't decoration — it IS the methodology.

## The Hierarchy

| Level | Scope | Artifact | Contains |
|-------|-------|----------|----------|
| **Warroom** | The endeavor | README.md (telos + campaign matrix) | Campaigns |
| **Campaign** (`c##-name/`) | Strategic push | README.md (lore + quest matrix + victory conditions) | Quests |
| **Quest** (`q##-name/`) | Deliverable goal | README.md (charter + mission matrix) | Missions |
| **Mission** (`m##-name.md`) | Tactical action | Self-contained file | (leaf) |

Warroom, campaigns, and quests are directories (places). Missions are files — completion = debrief + delete. The matrix is the memory.

## Core Mechanics

**Fog of War.** Unknown territory clears as you explore. Don't plan what fog hasn't revealed. Each completed mission shows what's next.

**Intel Flow.** Strategy flows DOWN (warroom to mission). Wisdom flows UP (mission to warroom). Classification: TACTICAL (stays) → OPERATIONAL (quest) → STRATEGIC (campaign) → DOCTRINAL (warroom).

**Campaign Design.** Campaigns are strategic pushes, not organizational categories. Victory conditions, time horizon, 3-7 quests. "Development" is a filing cabinet. "Ship the agent species" is a campaign.

**Narrative Engagement.** Lore sections make quests meaningful. Victory conditions make completion feel like winning. The RPG frame turns "project status meeting" into "checking the quest log."

## Organism-Aware

QuestForge loads into an organism with faculties already present. It owns the PM methodology — hierarchy, intel flow, narrative, campaign/quest/mission design. The faculties handle memory (anamnesis), spawning (embodiment), and evolution (plasticity). No duplication.

## Package

```
app/quest-forge/
  atom.xml    # Monolithic (abstract + concrete)
  README.md   # This file
```

## Install

```
bentos-agent pkg install quest-forge.app
```
