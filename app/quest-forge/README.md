# QuestForge

**FQDN:** `quest-forge.app`
**Kind:** Living Application

*Warroom discipline for work that matters.*

---

## What it is

QuestForge is a discipline for running complex, multi-session work. **Campaigns push. Quests deliver. Missions execute. Rounds engage.** Every level is a living story that grows as real events unfold — no speculation, no deletion, no lost wisdom.

The RPG vocabulary isn't decoration; it IS the methodology. "Quest log" organizes differently than "task list." "Fog of war" plans differently than "requirements." "Victory conditions" end differently than "targets." Each word shapes how work gets thought about, and thereby how it gets done.

Underneath the narrative is a **cooperative-execution model**: missions are functions that return; quests await missions; campaigns await quests. Work is already async in practice — QuestForge gives it vocabulary, so the async execution becomes legible instead of implicit. A warroom is a natural-language stack trace of the work in flight.

Work framed as adventure gets finished.

**Who it's for.** Solo founders holding a product in their head. Teams coordinating across weeks and months. AI agents threading complex endeavors across sessions. If the work would benefit from you looking back in three months and understanding how you got here, it belongs in a warroom.

---

## What it cures

QuestForge exists because complex work fails in predictable ways:

- **Speculation masquerading as planning.** Drafting twelve missions when one has landed. Writing requirements documents for territory you haven't explored.
- **Lost wisdom.** Hard-won insights from one piece of work failing to reach the next. The field report deleted because the mission "completed."
- **Permanent projects.** "Development" that never ends, because it was never scoped as a push with a condition that can be WON.
- **Mechanical execution.** Troops spawned without briefing, cut off from comms, expected to return with answers to questions no one asked them.
- **Untracked async.** Multiple missions in flight, attention shifting across quests, decisions cascading across levels — but no vocabulary to express it. What's blocked on what lives in people's heads.
- **Narrative death.** Work that devolved into grind because someone lost the plot.

Each of these has a specific antidote in QuestForge's structure. The rest of this document names those antidotes.

---

## The hierarchy

Four levels of structure. One level of execution. Each level is self-similar — same pattern, smaller scope.

| Level | Scope | Typical duration | Artifact |
|---|---|---|---|
| **Warroom** | The endeavor | Years | `README.md` — telos + campaign matrix + progress + key discoveries |
| **Campaign** (`c##-name/`) | Strategic push | Weeks to months | `README.md` — telos + quest matrix + victory conditions + progress + key discoveries |
| **Quest** (`q##-name/`) | Deliverable goal | Days to weeks | `README.md` — charter + mission matrix + active landscape + progress + key discoveries |
| **Mission** (`m##-name.md`) | Tactical action | One or more sessions | Self-contained living file — charter + success criteria + deliverables + progress + knowledge |
| **Round** | Engagement | One context window | Narrative chapter within a mission's Progress section |

Warroom, campaigns, and quests are **places** — directories with a `place.yaml`. Missions are **files**. Rounds are **chapters inside mission files** — never their own artifact, never a directory of briefing/digest pairs.

**Numbering:** `c##` global across the warroom; `q##` per campaign; `m##` per quest; `r#` within a mission. Small numbers. No sub-numbering unless you genuinely need it.

---

## States

| State | In-world | Meaning |
|---|---|---|
| 🔒 **BLOCKED** | Door locked — need a key | Prerequisites not met |
| 🗺️ **REVEALED** | New area on the map | Ready to start |
| ⚔️ **ACTIVE** | Currently exploring | In progress |
| 🏆 **COMPLETE** | Victory | Delivered; intel bubbled; story finalized |
| 💀 **FAILED** | Defeated | Ended without delivering; postmortem is the return value |
| 🏳️ **ABANDONED** | Left the dungeon | Closed without finishing; preserved as historical record |

States apply at every level. A FAILED mission is as legitimate an outcome as a COMPLETE one — work doesn't always succeed, and honest tracking requires naming that. An ABANDONED campaign is preserved, not deleted — the story of why it was abandoned is institutional wisdom.

**Visual semantics.** QuestForge's discrete states, action verbs, intel classifications, and fog zones all carry an emoji. This is not decoration — humans are visual beings, and an emoji-prefixed enum scans at a glance in a way a bare word does not. The emoji IS the value; the word IS the value. Machine and human read the same semantic, encoded twice. Use the emoji anywhere the enum appears: matrix status columns, action blockquotes, classification tags on Key Discoveries, fog markers in landscape notes.

---

## Living stories

Every level is an **autobiography**. It grows as the mission, quest, or campaign lives. Past persists. Present is current. Future is fog — acknowledged, never filled with speculation.

A warroom README tells the endeavor's story. A campaign README tells the campaign's story. A quest README tells the quest's story. A mission file tells the mission's story. The pattern is fractal — same shape, tighter scope at each level.

**Nothing gets deleted to clean up.** A mission file that matured into a 140-line field report is not bloat; it IS the mission's autobiography, load-bearing for sibling missions, for parent-quest debrief, for cross-campaign pattern-finding. The matrix is an index, not a replacement for the story.

**Progress is where the story unfolds.** Every level has a Progress section. Everything else is either aspirational (charter, victory conditions) or context (prior art, matrices). Progress is the living, present-tense record of what actually happened — narrative prose interleaved with action blockquotes that carry the execution timeline. At campaign scope, Progress naturally accretes into named narrative arcs (what other systems might call "lore"). At mission scope, it reads as round-by-round unfolding. Same section, scope-appropriate tone.

**Files start small and grow.** A new campaign README has telos + empty matrices + victory conditions + empty Progress. Each session that advances the campaign adds real events — never speculation. Key Discoveries are chronological, each entry carrying session provenance (`S###`) and an intel classification. They form the timeline of how understanding evolved.

---

## Fog of war

Unknown territory clears as you explore. **Plan only what fog has revealed.**

Three zones:

| Zone | State | What you do |
|---|---|---|
| ⬛ **BLACK** | Can't see terrain | Send recon — a mission to clear it |
| 🌫️ **FOG** | Can see terrain, can't see specifics | Execute — the work reveals specifics |
| ☀️ **VISIBLE** | Can see it | Move on — don't re-examine what you already know |

Fractal at every scale — fog exists at warroom level (which campaigns come next?), at campaign level (which quests?), at quest level (which missions?), at mission level (which rounds?).

**Questions emerge from walls, not from speculation.** When you hit a real wall — a decision you cannot make, a dependency you cannot resolve — that's ONE question, filed precisely at the appropriate level. "Nine open questions" is the signature of asking about what's behind the fog. If you can't ask the question precisely, you haven't reached the wall yet.

**Missions are for execution.** They carry charters, deliverables, verifiable outcomes. Questions live at quest level or higher. A completed mission delivers ANSWERS — it does not emit a list of new unanswered questions. If it did, the mission was scoped as exploration rather than execution, and needs re-forging.

---

## Actions — the cooperative-execution model

Strategic and tactical framings tell you WHAT the work is. The operational layer tells you HOW the work RUNS in wallclock time — what's in flight, what's blocked on what, what has returned, what failed, what got garbage-collected.

That layer comes naturally once you see the work for what it is: a functional program told as a story.

### Work runs async

Missions are functions. They have inputs (charter, deliverable slots). They have outputs (filled deliverables). They **yield** between rounds. They **return** on completion — with success, with failure, or with abandonment. Quests call missions. Campaigns call quests.

```
campaign.run()
  → quest.run()
      → mission.run()
          → round() → yield
          → round() → yield
          → return(complete | failed | abandoned)
      → return(complete | failed | abandoned)
  → return(complete | failed | abandoned)
```

The daily reality of running a warroom is already async — missions in flight concurrently, attention shifting between quests, decisions cascading across levels. QuestForge's job is to give that reality **vocabulary and structure**, so the async execution becomes legible instead of implicit.

### Actions: the synchronization primitive

Inside any level's `Progress` section, prose narrates the story; **action blockquotes** punctuate with structured events. The syntax:

```markdown
> **verb** `object` — prose context
```

An action carries function-call energy: a verb naming the operation, an object (what's acted on), and prose explaining the context.

Examples drawn from a live warroom:

```markdown
> ⚒️ **forged** `m02-scaffold` — Rust crate + first cluster wired end-to-end

> ⚡ **decided** `authority-model` — .xml = schema truth, .md = semantics truth

> ⏳ **awaiting** `q04/m02` — John on field; returns next session

> ▶️ **engaged** `r3` — teammate: alfred-benstack-01; briefing attuned

> 🪂 **landed** `r3` — BUMP_SIZE wall hit, patched to 32000, device boots clean

> 🏆 **complete** `m01-spine` — full specification, 6 artifacts, skeleton exceeded

> 💀 **failed** `m03-wifi-bridge` — rs-matter API churn; revisit after 0.2

> 🏳️ **abandoned** `q05-gui-prototype` — subsumed by q07 after strategic reframe
```

Scanning the Progress section visually surfaces the execution timeline. A reader sees at a glance what was dispatched, what returned, what's in flight.

### Core verbs

Eight verbs. Learn them once; they apply at every level.

| Verb | Semantics | Applies at |
|---|---|---|
| ⚒️ **`forged`** | Created / dispatched — a child begins to exist | Warroom (campaign), Campaign (quest), Quest (mission) |
| ▶️ **`engaged`** | Round starts — teammate spawned, briefing attuned, work begun | Mission (round) |
| 🪂 **`landed`** | Round yields — teammate returns, chapter written, mission resumes | Mission (round) |
| ⏳ **`awaiting`** | Blocking state — parent is waiting on a child's return | Any level awaiting a child |
| ⚡ **`decided`** | Synchronization point — a choice affecting scope, sequencing, or strategy | Any level |
| 🏆 **`complete`** | Successful return — deliverables filled, verification passed | Mission, Quest, Campaign |
| 💀 **`failed`** | Error return — walls too high, premise wrong, blocker insurmountable | Mission, Quest, Campaign |
| 🏳️ **`abandoned`** | Garbage-collected return — scope moved elsewhere, obsoleted by intel | Mission, Quest, Campaign |

Note: the three return-mode verbs share emojis with the resulting states. That's intentional — the action fires, the state updates, the same semantic is encoded.

**Three return modes.** `complete`, `failed`, `abandoned` — honest tracking requires all three. "Every mission completes" is aspirational fiction. A `failed` mission is not a shameful outcome; it is a return value, and it feeds parent-level replanning. An `abandoned` mission is explicit garbage collection — the file persists as historical record, but the mission is closed.

### The stack trace effect

A warroom is a live call stack of files:

- **Warroom README** — top frame. Its Progress logs campaign-level actions.
- **Campaign README** — next frame. Its Progress logs quest-level actions.
- **Quest README** — next frame. Its Progress logs mission-level actions.
- **Mission file** — leaf frame. Its Progress logs round-level actions and the final return.

Navigating a live warroom IS navigating a stack trace. An `awaiting` at campaign level points to a quest in flight; descend into the quest README and you see what that quest is blocked on; descend into the mission and you see its rounds. Each action names the level below; each return propagates the level above.

This is the **synchronization primitive QuestForge has been missing**. You now have return paths, await points, garbage-collection markers, decision boundaries — all in natural language, all filesystem-navigable.

### When to use actions

Not every sentence in Progress needs a blockquote. Narrative prose carries the story; action blockquotes punctuate with **events that matter to the execution timeline**:

- A mission/quest/campaign was forged
- A return happened (complete / failed / abandoned)
- A round engaged or landed
- A decision was made that affects scope, sequencing, or strategy
- Something is being explicitly awaited

Conversational narrative stays prose. A round that ran three experiments, narrated in paragraph form, ends with:

```markdown
> 🪂 **landed** `r3` — three experiments; only the third produced the shape we needed
```

The prose tells the story; the action marks the timeline beat.

---

## Rounds — the unit of execution

A round is the mission-level form of an action: **one teammate, one context window, one coherent piece of work**. A mission worth running is usually too big for a single round; round cadence is how missions span sessions.

### Rounds are narrative chapters inside the mission's Progress section

Not separate files. Not briefing/digest pairs. The mission file IS the briefing; the round's outcome metabolizes back into the mission file in-place — deliverable slots fill, Progress narrates what happened, `engaged` and `landed` actions bracket the chapter.

A chapter title reads as a **story beat**, with the round number suffixed:

```markdown
## Progress

### Package skeleton lands (r1)
(narrative prose of what happened)

> ▶️ **engaged** `r1` — teammate: alfred-m03-01; briefing attuned
> 🪂 **landed** `r1` — package compiles; version test passes; zero warnings

### BUMP_SIZE wall, stack wired (r3)
(narrative prose)

> ▶️ **engaged** `r3`
> 🪂 **landed** `r3` — BUMP_SIZE=20000 panics on macOS debug; patched to 32000
```

Not `### Round 1: Package Skeleton`. Narrative first, numbering second. The Progress section reads top-to-bottom as the story of the mission, not as a process log.

### Interactive troops, always

A round is executed by a teammate spawned **interactively** — comms line open, general reachable, teammate reachable. Never background. Never fire-and-forget.

The Pentagon does not deploy a recon team and cut radio contact; neither do we.

### Briefing is attunement, not fire-and-forget

The teammate's first act is reading the mission file and confirming alignment with the general. If there's a seam — a charter that isn't precise, a deliverable that doesn't fit one round, a scope that's ambiguous — the teammate surfaces it BEFORE engaging. Attunement before engagement, always. A briefing that doesn't invite attunement pushback is a spawn, not a briefing.

The `engaged` action is issued ONLY after attunement is confirmed.

### Round cadence is emergent

The first round is always concrete and precisely scoped. Subsequent rounds emerge from what each round reveals. Front-loading a six-round plan speculates about walls you haven't reached; planning r2 once r1's chapter is written keeps you honest with the fog.

A mission's deliverable list may be planned upfront — those are the slots. The round cadence that fills them is emergent.

---

## Intel flow

Strategy flows DOWN. Wisdom flows UP.

| Classification | Scope | Lives at |
|---|---|---|
| 🔬 **TACTICAL** | This mission only | Stays in the mission file |
| ⚙️ **OPERATIONAL** | This quest | Quest README — Key Discoveries |
| ♟️ **STRATEGIC** | This campaign | Campaign README — Key Discoveries |
| 📜 **DOCTRINAL** | The whole endeavor | Warroom README — Key Discoveries |

Key Discoveries entries carry their classification emoji as a prefix, alongside session provenance. A load-bearing turning point that reshaped a campaign reads as `♟️ S350` with the discovery's narrative following. Salience markers (🎯 for turning points, 🔴 for blockers) may prefix entries that warrant them — orthogonal to classification, both can appear.

Classification is **continuous** — as intel surfaces, classify and route it. Not bookend, not terminal archive. Most intel is TACTICAL; resist over-promotion. A discovery that reshapes the campaign is doctrinal; a discovery about a specific file is tactical. Calibrate.

**Debrief is continuous metamorphosis**, not a terminal archive act. Intel surfaces throughout execution. Completion-time debrief is the final beat of a process that's been running the whole time — finalize the file, update the parent matrix, ensure OPERATIONAL-and-above intel has bubbled. The file persists as autobiography.

---

## File shapes

Each level's file follows a consistent structure — aspirational content up front, static references in the middle, and **Progress** as the living timeline where the story unfolds.

### Warroom README

```markdown
# [Warroom Name]

## Telos
One sentence: what this endeavor IS.

## Campaign Matrix
| ##  | Campaign             | Victory Condition                 | Status          |
|-----|----------------------|-----------------------------------|-----------------|
| c01 | foundations          | agent species shipped             | 🏆 COMPLETE     |
| c04 | benstack             | first paying customer             | ⚔️ ACTIVE       |
| c05 | hosted-paas          | multi-tenant tier live            | 🔒 BLOCKED      |

## Progress
The endeavor as it unfolds — narrative prose with campaign-level actions.

> ⚒️ **forged** `c04-benstack` — the money path
> ⚡ **decided** `matter-is-substrate` — Resolution B; applies across c04
> 🏆 **complete** `c03-agent-species` — agent architecture shipped
> ⏳ **awaiting** `c04-benstack` — critical path; all other campaigns deprioritized

## Key Discoveries
📜 DOCTRINAL intel. Chronological, with session provenance.
```

### Campaign README

```markdown
# c## — [Name]

## Telos
One sentence: what this campaign IS within the endeavor.

## Quest Matrix
| ## | Quest | Goal | Status | Outcome |

## Victory Conditions
- [ ] Measurable condition 1
- [ ] Measurable condition 2

## Progress
The campaign as it unfolds — narrative arcs, turning points, pivots.
Quest-level actions punctuate the story.

### The Matter recognition (S341)
(prose narrative of the turning point)

> ⚡ **decided** `matter-is-substrate` — Resolution B; LightMatter retired

### The spec arc (S353–S354)
(prose narrative)

> ⚒️ **forged** `q02/m01` — co-author device + cluster libraries
> 🏆 **complete** `q02/m01` — full spec, 6 artifacts, skeleton exceeded
> ⚒️ **forged** `q02/m02` — Rust crate + first cluster wired
> ⏳ **awaiting** `q02/m02` — in flight

## Key Discoveries
♟️ STRATEGIC intel bubbled from quests.
```

### Quest README

```markdown
# q## — [Name]

## Charter
What this quest delivers. Why. Scope boundaries (IN / OUT).

## Mission Matrix
| ## | Mission | Goal | Status | Outcome |

## Active Landscape
Current state, blockers, priorities — updated each session.

## Progress
The quest as it unfolds — mission-level actions and their context.

> ⚒️ **forged** `m01-library-spine` — co-author device + cluster libraries
> ⚡ **decided** `three-cluster-decomposition` — VMM Host + Machine Mgmt + Capability
> 🏆 **complete** `m01-spine` — full spec delivered; exceeded skeleton charter
> ⚒️ **forged** `m02-scaffold` — Rust crate + first cluster wired
> ⏳ **awaiting** `m02-scaffold` — in flight

## Key Discoveries
⚙️ OPERATIONAL intel bubbled from missions.
```

### Mission file

```markdown
# m## — [Name]

## Charter
What this mission delivers. Why. Scope boundaries.

## Success Criteria
Outcome-shaped, verifiable, binary. Tied to deliverables, not activities.

## Deliverables
Named slots. Each slot sized to fit one round. Filled in-place as rounds land.

## Progress
The story as it unfolds — rounds as narrative chapters with actions.

### Package skeleton lands (r1)
(narrative prose)

> ▶️ **engaged** `r1` — teammate: alfred-m03-01; briefing attuned
> 🪂 **landed** `r1` — package compiles; version test passes; zero warnings

### Fork context from humanos (r2)
(narrative prose)

> ▶️ **engaged** `r2`
> 🪂 **landed** `r2` — AgentCtx + ContextMsg forked; tests green

### Final return
> 🏆 **complete** `m03-scaffolding` — package runs; all success criteria met

## Knowledge
Durable intel accumulated. 🔬 TACTICAL stays. ⚙️ OPERATIONAL+ also bubbles.
```

**There is no Open Questions section** at mission level. Ever. Questions hit walls at quest level or higher.

---

## Artifacts on disk

A warroom after a few months of work looks like this:

```
warroom/
  README.md                           # endeavor telos + progress + doctrinal intel
  c01-foundations/
    README.md                         # campaign telos + progress + strategic intel
    q01-something/
      README.md                       # quest charter + progress + operational intel
      m01-first-mission.md            # living file — charter + rounds + knowledge
      m02-second-mission.md
    q02-something-else/
      README.md
      m01-...md
  c02-next-push/
    README.md
    q01-...
```

**Deliverables go where they're consumed** — code into the codebase, specs into the package they spec, docs into where readers find them. The warroom TRACKS; it doesn't STORE. If a deliverable is truly orphaned (nowhere natural to live), a quest-level `deliverables/` directory accommodates it.

Mission files persist. They are the autobiography of the work at its most concrete layer.

---

## What it is NOT

QuestForge is distinguished from superficially similar systems by what it refuses to be.

- **Not a TODO app.** TODO apps track atomic tasks without narrative. QuestForge tracks stories with structure, and events with execution semantics. A task list is a flat enumeration; a quest log is a stack trace.
- **Not gamification.** Gamification bolts game mechanics onto unrelated work. QuestForge uses RPG vocabulary because the vocabulary shapes thought — "side quest" entered common language because the metaphor is powerful. Methodology, not decoration.
- **Not agile ceremonies.** No sprints, no standups, no retros-as-ritual. Cadence emerges from the work, not from the calendar. Debrief is continuous, not scheduled.
- **Not a filing system.** The warroom is mission control, not a cabinet of archived projects. The active view shows what's ACTIVE or REVEALED. History lives in the living stories and in git.
- **Not a planning tool.** QuestForge resists planning past the fog. The method is exploration, not forecasting. A Gantt chart is a confidence-trick played on uncertain terrain; a quest log is a record of the terrain you've actually covered.

---

## Design commitments

Principles that apply at every level:

- **Fractal self-similarity.** Warroom, campaign, quest, mission — same pattern, smaller scope. Learn the pattern once.
- **Living stories.** README and mission files are autobiographies. They grow as real events unfold; they don't get deleted to clean up.
- **Progress is present-tense.** Everything else is aspirational or context. Progress is where the story actually happens.
- **Actions are the synchronization primitive.** Every dispatch, return, yield, and decision surfaces as a blockquote action. The warroom becomes a natural-language stack trace.
- **Visual semantics.** Discrete states, actions, classifications, and fog zones carry emojis. The emoji IS the value. Humans scan; machines parse; both read the same semantic.
- **Three return modes.** 🏆 `complete`, 💀 `failed`, 🏳️ `abandoned`. Honest tracking requires all three.
- **Interactive execution.** Troops always in comms with their general. Never fire-and-forget. Attunement before engagement.
- **Fog of war.** Plan only what fog has revealed. Questions emerge from walls, not speculation.
- **Continuous debrief.** Classify intel as it surfaces. Route it to the right height. Most is TACTICAL.
- **Lean warroom.** Mission control, not filing cabinet. The active view shows only what's ACTIVE or REVEALED.
- **Work at target.** Deliverables go where they're consumed. The warroom tracks; it doesn't contain work product.
- **Narrative as methodology.** The RPG frame IS the methodology. Vocabulary shapes thought.

---

## Install

```
bentos-agent pkg install quest-forge.app
```

QuestForge is a Living Application loaded into an agent's context. It provides the PM discipline; the organism's faculties (anamnesis, embodiment, plasticity) handle memory, spawning, and evolution. QuestForge owns the methodology; it does not own the cognitive infrastructure.

Humans can adopt QuestForge without the atom — everything in this spec is filesystem-level conventions, executable by hand, by agent, or by any combination. The atom is what makes the methodology native to an agent's cognition.

---

## Package

```
app/quest-forge/
  atom.xml    # Monolithic (living-abstract + living-concrete)
  README.md   # This file — the product spec
```

The atom is the implementation truth. This README is the definition.
