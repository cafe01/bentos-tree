# QuestForge

**FQDN:** `quest-forge.app`
**Kind:** Living Application

*Situation room above, living story below. Warroom discipline for work that matters.*

---

## What it is

**QuestForge is warroom discipline** — a methodology that **turns complex, multi-session endeavors into legible warrooms**: situation-room dashboards for present-time action, backed by living stories that grow as real events unfold.

Four fractal levels of structure, one level of execution:

**Campaigns push. Quests deliver. Missions execute. Rounds engage.**

Underneath the narrative is a **cooperative-execution model**: missions are functions that return; quests await missions; campaigns await quests. Work is already async in practice — QuestForge gives it vocabulary and UI so the async becomes legible instead of implicit. **A warroom is a natural-language stack trace.**

**QuestForge is also a Living Application.** Its current body is a skill atom + markdown conventions; its future body is native Flutter widgets + Agentic HUD integration + an Agent Core (the Dungeon Master). The atom authored today IS the brain of the future binary — same soul, evolving surface. The methodology survives the platform journey.

**Who it's for.** Solo founders holding a product in their head. Teams coordinating across weeks and months. AI agents threading complex endeavors across sessions. If the work would benefit from walking into a situation room and reading the board before acting, it belongs in a warroom.

---

## What it cures

Complex work fails in predictable ways. QuestForge exists to name the antidotes.

- **Speculation masquerading as planning.** Drafting twelve missions when one has landed. Writing requirements for territory you haven't explored.
- **Lost wisdom.** Hard-won insights from one piece of work failing to reach the next. The field report deleted because the mission "completed."
- **Permanent projects.** Development that never ends, because it was never scoped as a push with a condition that can be WON.
- **Mechanical execution.** Troops spawned without briefing, cut off from comms, expected to return with answers to questions no one asked them.
- **Untracked async.** Multiple missions in flight, attention shifting across quests, decisions cascading — but no vocabulary. What's blocked on what lives in people's heads.
- **History obscuring present.** Chronological logs where current truth should live. The general can't read the board because the board is a diary.
- **Document bloat.** Files growing without curation discipline until nobody can find what's true now.
- **Narrative death.** Work that devolved into grind because someone lost the plot.

Each has a specific antidote in QuestForge's structure. The rest of this spec names them.

---

## The hierarchy

Four levels of structure. One level of execution. Each level is self-similar — same pattern, tighter scope.

| Level                       | Scope            | Typical duration     | Artifact                                                    |
| --------------------------- | ---------------- | -------------------- | ----------------------------------------------------------- |
| **Warroom**                 | The endeavor     | Years                | `README.md` — endeavor dashboard + progress                 |
| **Campaign** (`c##-name/`)  | Strategic push   | Weeks to months      | `README.md` — campaign dashboard + progress                 |
| **Quest** (`q##-name/`)     | Deliverable goal | Days to weeks        | `README.md` — quest dashboard + progress                    |
| **Mission** (`m##-name.md`) | Tactical action  | One or more sessions | Self-contained file — mission dashboard + progress          |
| **Round**                   | Engagement       | One context window   | Narrative chapter within a mission's Progress section       |

Warroom, campaigns, and quests are **places** — directories with a `place.yaml`. Missions are **files**. Rounds are **chapters inside mission files** — never their own artifact, never a directory of briefing/digest pairs.

**Numbering:** `c##` global across the warroom; `q##` per campaign; `m##` per quest; `r#` within a mission. Small numbers. No sub-numbering.

---

## Visual semantics — emojis as icon font

QuestForge's `.md` files are the source for a rendered UI. Think HTML for today's text-first body. **Unicode glyphs are our icon font** — the equivalent of Font Awesome or Material Icons for a markdown-rendered target.

This has a strict consequence: **every glyph must pass the 16×16 UI test**. Shape and color survive downscaling; literal illustrations don't. A parachute, a skull, a trophy at 16 pixels are blobs whose meaning lives in the Unicode name, not the pixels. A red circle, a green check, a blue filled shape survive at any size — color is the primary information carrier, shape adds semantic.

The design principle: **choose glyphs the way a UI/UX designer chooses icons**, not the way a thesaurus matches concepts to Unicode descriptions. Red = bad. Green = good. Yellow = caution. Blue = neutral-active. Gray = inert. Add geometric shapes (circle, check, X, triangle) for the semantic layer.

**The emoji IS the value; the word IS the value.** Machine and human read the same semantic, encoded twice. Use the glyph wherever the enum appears — matrix state columns, situation status, intel salience, action blockquotes.

---

## States — the primary enum

Every dashboard uses these six glyphs. They appear in Matrix state columns, Situation entries, and action returns.

| State         | Glyph | In-world            | Meaning                                                  |
| ------------- | :---: | ------------------- | -------------------------------------------------------- |
| **BLOCKED**   |  🔴   | Door locked         | Prerequisites not met                                    |
| **REVEALED**  |  🟡   | New area on the map | Ready to engage                                          |
| **ACTIVE**    |  🔵   | Currently exploring | In flight                                                |
| **COMPLETE**  |  ✅   | Victory             | Delivered; intel bubbled; story finalized                |
| **FAILED**    |  ❌   | Defeated            | Ended without delivering; postmortem is the return value |
| **ABANDONED** |  ⚫   | Left the dungeon    | Closed without finishing; preserved as historical record |

Traffic-light colors carry the progress semantic (stop / prep / in-flight). Check and X carry the binary-outcome semantic. Gray circle carries the closed-without-verdict semantic.

States apply at every level. A FAILED mission is as legitimate an outcome as a COMPLETE one — work doesn't always succeed, and honest tracking requires naming that. An ABANDONED campaign is preserved, not deleted — the story of why it was abandoned is institutional wisdom.

---

## Anatomy of a file — dashboard above, story below

Every QuestForge file has two zones:

**1. The Dashboard** (everything above Progress) — the situation-room view. A general walks in, scans the board, and has everything needed to act NOW. Present-tense intel, current state, what's hot right now. **Self-sufficient for present-time action.**

**2. Progress** (the last section) — the living story. Autobiography of the work. Append-only, chronological, narrative. Load-bearing for archaeology, parent-level debrief, cross-session pattern-finding — but **not required to keep pushing.**

### Sections as memory types

Each dashboard widget has a curation discipline tied to a specific memory type. Know the type, know how to curate.

| Widget                                      | Memory type         | Discipline                                                                                        | Grows?                            |
| ------------------------------------------- | ------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------- |
| **Identity** (Telos · Charter · Victory)    | Identity            | Near-immutable. Changes only by deliberate reframe.                                               | No                                |
| **Matrix** (child state table)              | Structural ledger   | Rows append-only. Cells update to final state. NEVER delete rows.                                 | Yes, bounded by children spawned  |
| **Situation** (linked live items)           | Episodic            | Rewritten each session. LIVE items only (🔵 / 🟡 / ⏳). Closed items drop off.                    | No (session-capped)               |
| **Intel** (present-tense truths)            | Semantic            | Present-tense doctrine. Curated. No chronology. No session provenance. Origin-links on promoted. | Slow, bounded by scope            |
| **Progress** (narrative timeline)           | Autobiographical    | Append-only narrative. Rounds as chapters. Linked mentions.                                       | Unbounded (the story)             |

**Prospective memory is implicit in the fractal.** A quest's missions ARE the quest's commitments to act. A campaign's quests ARE the campaign's commitments. The filesystem topology carries prospective — no separate section needed.

**Only two widgets grow:** Matrix (row per child) and Progress (narrative accretion). Both bounded by the work actually done. **The scaling law:** `runQuest()` adds a constant, not a slope, to dashboard reading cost. Progress is the unbounded section, and it's the skippable one.

---

## The dashboard widgets

### Identity — who this place is

Telos (one sentence for the endeavor/campaign), Charter (mission/quest definition with scope IN / OUT), Victory Conditions (measurable outcomes for a campaign — what winning looks like). Near-immutable. Changes only by deliberate reframe.

This is the **soul** widget — what this place IS, independent of what's happening in it.

### Matrix — the structural ledger

The canonical existence record of every child this level has commissioned. Rows append-only; cells update-only; never delete a row. A COMPLETE quest still occupies its row — the state cell just carries the final glyph.

```markdown
## Quest Matrix
| ##  | State | Quest                                              | Goal                                     |
| --- | :---: | -------------------------------------------------- | ---------------------------------------- |
| q01 | 🏳️    | [paas-domain](q01-paas-domain/)                    | Two university courses (abandoned S355)  |
| q02 | 🔵    | [benstack-app](q02-benstack-app/)                  | Rust lib/benstack on rs-matter(-stack)   |
| q03 | 🏳️    | [lightmatter-substrate](q03-lightmatter-substrate/)| Scope absorbed by q02 (abandoned S351)   |
| q04 | 🔵    | [rs-matter-evaluation](q04-rs-matter-evaluation/)  | Hands-on integration evidence            |
```

**State glyph is column 2** — the eye scans it early. Column 1 is the ID; columns 3+ are text. Outcome folds into State (the final glyph IS the outcome).

Matrix rows link to the child file/place — `[name](path)` — so the Matrix doubles as the navigation surface of the warroom's tree.

### Situation — the episodic live-briefing

The "what's hot right now" lens. Answers: *what's unblocked and ready to engage? what's burning? what's blocking? what's being awaited externally?*

One line per live item. Linked. Rewritten each session. Only 🔵 / 🟡 / ⏳ items appear — closed items drop off the Situation widget the moment they hit final state (they persist in Matrix and Progress).

```markdown
## Situation
- 🔵 [m02 lib/benstack scaffold](m02-scaffold.md) — r1 engaged; Rust crate up
- 🟡 [m03 wifi-bridge](m03-wifi-bridge.md) — revealed; awaiting m02 landing
- ⏳ [D2 ben exec decision](../workshop/d2-memo.md) — awaiting Boss authority
```

**Situation vs Matrix:** Matrix is the complete historical ledger (every child ever, including closed). Situation is the right-now briefing (only live items). Matrix persists; Situation refreshes.

**Situation vs Intel:** Situation is episodic (current-state snapshot, rewritten). Intel is semantic (durable truth, curated). A blocker belongs in Situation (current state); the WHY behind the blocker, if it's durable terrain knowledge, belongs in Intel.

### Intel — the semantic memory

Present-tense doctrine about the terrain at this scope. Not a log of events. Not "we discovered X at S350." Just current truth, scannable, curated.

```markdown
## Intel
- Matter is the substrate. `rs-matter` at [`cafe01/rs-matter`](https://github.com/cafe01/rs-matter) is the consumed fork.
- 🎯 Three-cluster decomposition: VMM Host, Machine Management, Capability Management.
- `MatterStack` is device-side only; Client role is bespoke on `rs-matter` primitives.
  [Origin: [q04/m02 r1](q04-rs-matter-evaluation/m02-stack-evaluation.md)]
- 🔴 `ben exec` is dogfooding-critical and has no direct Matter-IM analog.
  D2 decision artifact owns the resolution.
```

**Classification is encoded by level, not by in-band tags.** The file's level IS the classification:

| Level         | Intel classification | Mental model    |
| ------------- | -------------------- | --------------- |
| Mission       | Tactical             | 🔬              |
| Quest         | Operational          | ⚙️              |
| Campaign      | Strategic            | ♟️              |
| Warroom       | Doctrinal            | 📜              |

*(The emojis above anchor the mental model — they do NOT prefix entries. Prefixing with classification was a v1.0 pattern that retired: the file's level IS the tag.)*

**Salience markers** (orthogonal, used sparingly):
- 🔴 critical — urgent-now attention needed
- 🎯 turning-point — load-bearing moment in the record

**Intel flow — strategy down, wisdom up.** Strategy flows from warroom to campaign to quest to mission. Wisdom flows the other way. When a tactical finding matures into operational truth — when it affects more than this mission — it **relocates** to the quest file, rewritten in the higher voice, with an `[Origin: ...]` backlink to the source. When quest wisdom reshapes the campaign, it relocates again. Doctrinal truths that govern the whole endeavor live in the warroom README's Intel.

The discipline: **one intel, one home.** Zero duplication. The backlink preserves navigability — foreign-key discipline, Obsidian-vault energy.

Most intel is tactical. Resist over-promotion. A discovery that reshapes the campaign is doctrinal; a discovery about a specific file is tactical. Calibrate.

---

## Progress — the autobiography

Progress is where the story unfolds. Append-only. Chronological. Narrative prose interleaved with **action blockquotes** that carry the execution timeline.

Progress goes **LAST** on the page. The general doesn't need to read it to act on the current board; but it's load-bearing for archaeology, parent-level debrief, onboarding, and cross-session pattern-finding.

At warroom and campaign scope, Progress naturally accretes into **named narrative arcs** (what other systems might call "lore") — turning points, reframes, pivots, each with its own heading. At mission scope, Progress reads as **round-by-round unfolding** — each round is a chapter with a story-beat title. Same section, scope-appropriate tone.

**Nothing gets deleted to clean up.** A mission file that matured into a 140-line field report is not bloat; it IS the mission's autobiography, load-bearing for sibling missions and for parent-quest debrief. The Matrix is an index, not a replacement for the story.

---

## Actions — the cooperative-execution model

Strategic and tactical framings tell you WHAT the work is. The operational layer tells you HOW the work RUNS in wallclock time — what's in flight, what's blocked on what, what has returned, what failed, what got garbage-collected.

That layer comes naturally once you see the work for what it is: **a functional program told as a story.**

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

The daily reality of running a warroom is already async — missions in flight concurrently, attention shifting between quests, decisions cascading across levels. QuestForge gives that reality **vocabulary and structure**, so the async execution becomes legible instead of implicit.

### Actions are the synchronization primitive

Inside any level's Progress section, prose narrates the story; **action blockquotes** punctuate with structured events. The syntax:

```markdown
> **verb** `object` — prose context
```

An action carries function-call energy: a verb naming the operation, an object (what's acted on, `backticks`), and prose explaining the context. Scanning Progress visually surfaces the execution timeline — at a glance, a reader sees what was dispatched, what returned, what's in flight.

### Open verb vocabulary; conventional glyphs for stack-op categories

Actions are function calls — and function vocabulary is **open, not enumerated**. Real timelines have richer events than any closed verb list can cover: *investigated, discovered, reframed, pivoted, validated, rejected, escalated, deferred, merged, split, shipped, polished.* All legitimate timeline beats. All deserve to surface in Progress if they matter to the execution record.

What IS fixed is the set of **stack-operation categories** — the events that encode the call-stack semantics of the cooperative-execution model. These have conventional glyphs, used by strong convention across warrooms:

| Category            | Glyph | Natural verbs                                | Semantics                                                  |
| ------------------- | :---: | -------------------------------------------- | ---------------------------------------------------------- |
| **Dispatch**        |  ➕   | forged, spawned, created, commissioned       | A child begins to exist                                    |
| **Round-start**     |  ▶️   | engaged, opened, began, kicked-off           | Interactive round starts; teammate spawned                 |
| **Round-yield**     |  ◀️   | landed, yielded, returned                    | Round returns; mission resumes; chapter written            |
| **Await**           |  ⏳   | awaiting, waiting, blocked-on                | Parent blocks on a child's return                          |
| **Decision**        |  ◆    | decided, chose, committed                    | Synchronization point affecting scope / sequencing         |
| **Return-complete** |  ✅   | completed, shipped, delivered                | Successful return; deliverables filled                     |
| **Return-failed**   |  ❌   | failed, errored                              | Error return; walls too high, premise wrong                |
| **Return-abandoned**|  ⚫   | abandoned, cancelled, dropped                | Garbage-collected return; scope moved elsewhere            |

The pair **▶️ engaged** → **◀️ landed** creates visual parity — the round's "out" and "back" read as a matched set. The three return modes reuse state glyphs because action and resulting state encode the same semantic.

Beyond stack-ops, author glyphs by semantic family (red for problems, green for good, ⚠️ for warnings, 🔍 for investigation, 💡 for insight) or skip the glyph when prose carries the weight alone. The rule: **every blockquote signals a timeline beat; glyph earns its place by scan-value, never by obligation.**

Examples, drawn from a live warroom:

```markdown
> ➕ **forged** `m02-scaffold` — Rust crate + first cluster wired end-to-end
> ◆ **decided** `authority-split` — .xml owns schema, .md owns semantics
> ⏳ **awaiting** `q04/m02` — John on the field; returns next session
> ▶️ **engaged** `r3` — teammate: alfred-benstack-01; briefing attuned
> ◀️ **landed** `r3` — BUMP_SIZE wall hit; patched to 32000; device boots clean
> ✅ **complete** `m01-spine` — full specification; 6 artifacts; skeleton exceeded
> ❌ **failed** `m03-wifi-bridge` — rs-matter API churn; revisit after 0.2
> ⚫ **abandoned** `q05-gui-prototype` — subsumed by q07 after strategic reframe

> 🔍 **investigated** `MatterStack internals` — device-side only; client needs bespoke path
> 💡 **observed** `one-type-one-name pattern` — ResourceStruct unifies host + machine
```

### Three return modes

Honest tracking requires all three. *"Every mission completes"* is aspirational fiction. A FAILED mission is not a shameful outcome; it's a return value, and it feeds parent-level replanning. An ABANDONED mission is explicit garbage collection — the file persists as historical record, but the mission is closed without verdict on its outcome.

### The stack trace effect

A warroom is a live call stack of files:

- **Warroom README** — top frame. Its Progress logs campaign-level actions.
- **Campaign README** — next frame. Its Progress logs quest-level actions.
- **Quest README** — next frame. Its Progress logs mission-level actions.
- **Mission file** — leaf frame. Its Progress logs round-level actions and the final return.

Navigating a live warroom IS navigating a stack trace. An `⏳ awaiting` at campaign level points to a quest in flight; descend into the quest README and you see what that quest is blocked on; descend into the mission and you see its rounds. Each action names the level below; each return propagates the level above.

This is the **synchronization primitive QuestForge has been missing in legacy PM tools.** You now have return paths, await points, garbage-collection markers, decision boundaries — all in natural language, all filesystem-navigable.

### When to use actions

Not every sentence in Progress needs a blockquote. Narrative prose carries the story; action blockquotes punctuate with **events that matter to the execution timeline**:

- A mission / quest / campaign was forged
- A return happened (complete / failed / abandoned)
- A round engaged or landed
- A decision was made that affects scope, sequencing, or strategy
- Something is being explicitly awaited

Conversational narrative stays prose. A round that ran three experiments, narrated in paragraph form, ends with:

```markdown
> ◀️ **landed** `r3` — three experiments; only the third produced the shape we needed
```

The prose tells the story; the action marks the timeline beat.

---

## Rounds — the unit of execution

A round is the mission-level form of an action: **one teammate, one context window, one coherent piece of work.** A mission worth running is usually too big for a single round; round cadence is how missions span sessions.

### Rounds are narrative chapters inside the mission's Progress

Not separate files. Not briefing/digest pairs. The mission file IS the briefing; the round's outcome metabolizes back into the mission file in-place — deliverable slots fill, Progress narrates what happened, `▶️ engaged` and `◀️ landed` actions bracket the chapter.

A chapter title reads as a **story beat**, with the round number suffixed:

```markdown
## Progress

### Package skeleton lands (r1)
Short narrative of what happened. The teammate found X; we decided Y; the
unexpected wall was Z.

> ▶️ **engaged** `r1` — teammate: alfred-m03-01; briefing attuned
> ◀️ **landed** `r1` — package compiles; version test passes; zero warnings

### BUMP_SIZE wall, stack wired (r3)
Narrative continues.

> ▶️ **engaged** `r3`
> ◀️ **landed** `r3` — BUMP_SIZE=20000 panics on macOS debug; patched to 32000
```

Narrative first, numbering second. Progress reads top-to-bottom as the story of the mission, not as a process log.

### Interactive troops, always

A round is executed by a teammate spawned **interactively** — comms line open, general reachable, teammate reachable. Never background. Never fire-and-forget.

**The Pentagon does not deploy a recon team and cut radio contact; neither do we.**

### Briefing is attunement, not fire-and-forget

The teammate's first act is reading the mission file and confirming alignment with the general. If there's a seam — a charter that isn't precise, a deliverable that doesn't fit one round, a scope that's ambiguous — the teammate surfaces it **BEFORE** engaging.

Attunement before engagement, always. A briefing that doesn't invite pushback is a spawn, not a briefing. The `▶️ engaged` action is issued ONLY after attunement is confirmed.

### Round cadence is emergent

The first round is concrete and precisely scoped. Subsequent rounds emerge from what each round reveals. Front-loading a six-round plan speculates about walls you haven't reached; planning r2 once r1's chapter is written keeps you honest with the fog.

A mission's deliverable list may be planned upfront — those are the slots. The round cadence that fills them is emergent.

---

## Fog of war — the planning discipline

Unknown territory clears as you explore. **Plan only what fog has revealed.**

Three zones inform planning:

| Zone            | In-world                               | What you do                                   |
| --------------- | -------------------------------------- | --------------------------------------------- |
| **BLACK**       | Can't see terrain                      | Send recon — a mission to clear it            |
| **FOG**         | Can see terrain, can't see specifics   | Execute — the work reveals specifics          |
| **VISIBLE**     | Can see it                             | Move on — don't re-examine what you know      |

Fractal at every scale — fog exists at warroom level (which campaigns come next?), at campaign level (which quests?), at quest level (which missions?), at mission level (which rounds?).

**Missions are for execution**, not exploration. They carry charters, deliverables, verifiable outcomes. A completed mission delivers ANSWERS — it does not emit a list of new unanswered questions. If it did, the mission was scoped as exploration rather than execution, and needs re-forging.

**Questions emerge from walls, not from speculation.** When you hit a real wall — a decision you cannot make, a dependency you cannot resolve — that's ONE question, filed precisely at the appropriate level. *"Nine open questions"* is the signature of asking about what's behind the fog. If you can't ask the question precisely, you haven't reached the wall yet.

**Mission files carry no Open Questions section.** Ever. Questions live at quest level or higher, wall-positioned, singular.

---

## Linking — the Obsidian-vault discipline

**Every cross-file reference is a link.** The warroom is a knowledge graph, not a folder hierarchy.

- **Tree** for composition — warroom / campaign / quest / mission
- **Graph overlays** for data flow — promoted intel with provenance, cross-pollination between siblings, pointers to external prior art

Where linking applies:

- **Matrix rows** link to the child file or place
- **Situation entries** link to the live item
- **Intel entries** that originated elsewhere carry an `[Origin: ...]` backlink
- **Progress mentions** of other missions, quests, or campaigns always link
- **References** widgets are pure link lists

**Navigation IS UX.** Readers should never have to guess where something lives. Every claim with provenance carries its pointer. Backlinks make the graph walkable in both directions — the Obsidian-vault pattern, applied through standard markdown links. No wiki syntax, no plugins, no external infrastructure. Just `[text](path)` everywhere it earns its place.

---

## File shapes

Each level's file follows a consistent structure: **dashboard above, Progress below.** The dashboard composition varies per level; Progress is always last.

### Warroom README

```markdown
# [Warroom Name]

## Telos
One sentence: what this endeavor IS.

## Campaign Matrix
| ## | State | Campaign | Victory Condition |

## Situation
Live campaigns with state + brief note + link.

## Intel
Doctrinal truths about the endeavor (present-tense, curated).

## References
Static links to governing frames, upstream specs, authoritative artifacts.

## Progress
The endeavor as it unfolds — narrative prose with campaign-level actions.

> ➕ **forged** `c04-benstack` — the money path
> ◆ **decided** `matter-is-substrate` — Resolution B; applies across c04
> ✅ **complete** `c03-agent-species` — agent architecture shipped
```

### Campaign README

```markdown
# c## — [Name]

## Telos
One sentence: what this campaign IS within the endeavor.

## Victory Conditions
- [ ] Measurable condition 1
- [ ] Measurable condition 2

## Quest Matrix
| ## | State | Quest | Goal |

## Situation
Live quests with state + brief note + link.

## Intel
Strategic truths about the campaign (present-tense, curated;
origin-links on promoted items).

## References
Static links to campaign-level prior art.

## Progress
The campaign as it unfolds — narrative arcs, turning points, pivots.
Quest-level actions punctuate the story.
```

### Quest README

```markdown
# q## — [Name]

## Charter
What this quest delivers. Why. Scope boundaries (IN / OUT).

## Mission Matrix
| ## | State | Mission | Goal |

## Situation
Live missions with state + brief note + link.

## Intel
Operational truths about the quest's terrain (present-tense, curated).

## Progress
The quest as it unfolds — mission-level actions and their context.
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

## Intel
Tactical truths accumulated during execution (present-tense;
stays here unless promoted to quest level).

## Progress
The story as it unfolds — rounds as narrative chapters with actions.

### Package skeleton lands (r1)
Narrative prose.

> ▶️ **engaged** `r1` — teammate: alfred-m03-01; briefing attuned
> ◀️ **landed** `r1` — package compiles; version test passes; zero warnings

### Final return
> ✅ **complete** `m03-scaffolding` — package runs; all success criteria met
```

A mission file has **no Matrix** (it has no child files — rounds live IN Progress). **No Situation** (the mission itself IS the current focus; Deliverables + live rounds carry what's hot). **No Open Questions** section, ever. **No Key Discoveries** section — chronological log is Progress's job; present-tense truth is Intel's job.

---

## Success criteria — traceability and voice

Mission success criteria are where ambition meets verification. Outcome-shaped and binary is necessary but not sufficient. Two further disciplines, applied at charter authoring time — never deferred to close.

### Traceability

Every criterion answers, for itself: **which parent victory condition does this advance, and how much?** The chain — mission SC → quest charter → campaign victory → warroom telos — must be walkable. *"12/12 KPIs green"* names no parent victory; *"the daemon reports actual host capacity, sourced from system query"* advances *"the operator trusts the artifact in production."* SC that don't trace are broken even when outcome-shaped and binary.

### Voice — stakeholder-prose-is-the-spec

When a mission's deliverable touches a **stakeholder** — any party who is not the author of sibling code: a user, developer, operator, partner, customer — the user-facing artifact (manual page, install guide, error message, API reference, onboarding flow) IS the specification. Implementation orbits the prose. SC reference the artifact and the stakeholder's behavior.

For **substrate** missions consumed only by sibling code (a parser, a codegen pass, an internal cluster handler), the stakeholder frame doesn't apply — *"the consumer's tests pass"* is honest there. The discipline applies wherever the deliverable touches someone outside the codebase. When in doubt, ask whether anyone outside the codebase observes the deliverable; if yes, stakeholder.

### The diagnostic test

> *Can the SC be satisfied by engineering output alone — tests, KPIs, abstractions, code that compiles?*

If yes, **and** the mission delivers a stakeholder surface, the SC are wrong. The pattern is self-confirming: engineering-shaped SC are satisfied by engineering-shaped work, and the cycle never invokes the stakeholder frame. The team ships round after round, all green, and never asks whether the artifact is usable.

The cure: rewrite SC invoking a person (*"a stranger,"* *"a developer,"* *"the operator"*), an artifact they read (*"the manual,"* *"the install page,"* *"the error message"*), or a behavior they observe (*"the rootfs is cloned,"* *"a login prompt appears,"* *"the troubleshooting cure cures"*). Or scope-shrink the mission to substrate-only.

### And at close

A quest or campaign closes when its parent victory condition has been advanced — not when its child matrix is all-green. The two measure different things. The check at every close: **has the stakeholder's situation actually changed?** If closure leaves the stakeholder unchanged, only children closed; the parent didn't.

The stakeholder never reads the success criterion; the stakeholder reads the artifact. Therefore: **for stakeholder missions, the artifact is the success criterion.**

---

## Artifacts on disk

A warroom after a few months of work:

```
warroom/
  README.md                         # endeavor dashboard + progress
  c01-foundations/
    README.md                       # campaign dashboard + progress
    q01-something/
      README.md                     # quest dashboard + progress
      m01-first-mission.md          # living file — mission dashboard + progress
      m02-second-mission.md
    q02-something-else/
      README.md
      m01-...md
  c02-next-push/
    README.md
    q01-...
```

**Deliverables go where they're consumed** — code into the codebase, specs into the package they spec, docs where readers find them. The warroom TRACKS; it doesn't STORE. If a deliverable is truly orphaned (nowhere natural to live), a quest-level `deliverables/` directory accommodates it.

Mission files persist as the autobiography of the work at its most concrete layer.

---

## What it is NOT

QuestForge is distinguished from superficially similar systems by what it refuses to be.

- **Not a TODO app.** TODO apps track atomic tasks without narrative or structure. QuestForge tracks stories with dashboards and execution semantics. A task list is a flat enumeration; a quest log is a stack trace.
- **Not gamification.** Gamification bolts game mechanics onto unrelated work. QuestForge uses RPG vocabulary because the vocabulary **shapes thought** — *"side quest"* entered common language because the metaphor is powerful. Methodology, not decoration.
- **Not agile ceremonies.** No sprints, no standups, no retros-as-ritual. Cadence emerges from the work, not the calendar. Debrief is continuous, not scheduled.
- **Not a filing system.** The warroom is mission control, not a cabinet of archived projects. Situation shows what's active; Matrix records what exists; History lives in Progress.
- **Not a planning tool.** QuestForge resists planning past the fog. The method is exploration, not forecasting. A Gantt chart is a confidence trick played on uncertain terrain; a quest log is a record of the terrain you've actually covered.
- **Not a document system.** A document grows by accretion. A warroom grows by discipline — each widget has a memory type, each has curation rules, each earns its place on the dashboard.

---

## Design commitments

Ten invariants. Named to match the atom's living-abstract; ordered by concern — structure, curation, execution, planning, location, rendering. Each has a fuller treatment earlier in this spec; this list is the table of contents.

**Structure**

- **Dashboard-first.** Situation room above; autobiography below. The general acts from the board, not the diary.
- **Fractal self-similarity.** Same pattern at every scope, tighter boundaries. Learn once, apply at every level.

**Curation**

- **Memory-type per widget.** Each section has a curation discipline tied to its memory type. Know the type, know how to curate.

**Execution**

- **Cooperative execution.** Actions are synchronization primitives. A warroom is a natural-language stack trace.
- **Three return modes.** Complete, failed, abandoned — all first-class. Honest tracking requires naming giving up.
- **Interactive execution.** Troops in comms with their general. Attunement before engagement. The Pentagon does not cut radio contact.

**Planning**

- **Fog of war.** Plan only what fog has revealed. Questions emerge from walls, not speculation.

**Verification**

- **SC traceability.** Every mission SC names the parent victory condition it advances. The chain mission → quest → campaign → telos is walkable.
- **Stakeholder prose is the spec.** For missions whose deliverable touches anyone outside the codebase, the user-facing artifact IS the specification. Engineering output alone cannot satisfy stakeholder SC.

**Location**

- **One intel, one home.** Promotion is relocation plus origin-link. No duplication. Obsidian-vault navigability.
- **Work at target.** Deliverables live where they're consumed. The warroom tracks; it doesn't store. Mission control, not filing cabinet.

**Rendering**

- **Visual semantics.** Glyphs are the icon font. Every glyph passes the 16×16 UI test. Emoji IS the value.

---

## Install

```
bentos-agent pkg install quest-forge.app
```

QuestForge is a Living Application loaded into an agent's context. It provides the PM discipline; the organism's faculties (anamnesis, embodiment, plasticity) handle memory, spawning, and evolution. QuestForge owns the methodology; it does not own the cognitive infrastructure.

Humans can adopt QuestForge without the atom — everything in this spec is filesystem-level conventions, executable by hand, by agent, or by any combination. The atom is what makes the methodology native to an agent's cognition.

---

## Roadmap

QuestForge's body evolves across the platform journey; the methodology does not.

| Stage            | Body                                                      | Rendering                                                   |
| ---------------- | --------------------------------------------------------- | ----------------------------------------------------------- |
| **Today**        | Skill atom + markdown files                               | TUI — markdown-as-UI source, rendered in editors / IDEs     |
| **Near future**  | `quest-forge.exe` on BentOS                               | GUI — Flutter widgets, Agentic HUD integration              |
| **Mature**       | LApp Store flagship; pre-installed in BentOS Linux distro | Full Quest Map visualizer; AI Dungeon Master agent core     |

The Living Application's components, sketched from the start: **Agent Core** (the Dungeon Master — strategic partner, context-aware assistant), **Visualizer** (the Quest Map — an interactive rendering of the warroom's tree and graph overlays), **Conversational Interface** (Agentic HUD tab — natural language as primary input), **Formal Identity** (BentosAppManifest + capabilities).

The atom authored today IS the brain of that future binary. Same soul. Evolving surface.

---

## Package

```
app/quest-forge/
  atom.xml        # Monolithic atom (living-abstract + living-concrete)
  README.md       # This file — the product spec
  notes/          # Design discussions and rewrite artifacts
```

The atom is the implementation truth. This README is the definition.

---

*QuestForge: campaigns push, quests deliver, missions execute, rounds engage. Situation room above, living story below.*
