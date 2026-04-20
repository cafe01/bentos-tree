# QuestForge README Rewrite — Design Notes

**Session:** S356
**Purpose:** Refine QuestForge product spec into the shape it deserves before the v2.0 README rewrite.
**Status:** Design decisions locked. Full-pass README rewrite pending.

---

## The load-bearing reframe

**QuestForge IS a Living Application.** Not a markdown discipline — an application running in its primitive body. The components we sketched a year ago still hold: Agent Core (Dungeon Master), Visualizer (Quest Map), Conversational Interface (Agentic HUD), Formal Identity (manifest). Today's body: a skill atom + markdown conventions. Tomorrow's body: `quest-forge.exe` — Flutter widgets, HUD integration, pre-installed in the BentOS Linux distro as one of its flagship LApps.

**The atom.xml authored today IS the brain of that future binary.** Same atom, different rendering surface. The spec is an application's soul + UI contract, not a methodology document.

Corollaries:
- **.md is source for rendered UI** — like .html is source for rendered web UI.
- **Unicode is our icon font** — like Font Awesome / Material Icons. Every glyph passes the 16×16 UI test (shape + color > Unicode-keyword).
- **Warroom energy = Palantir / NASA mission control / situation-room.** At-a-glance intel, not document reading.

---

## Core design decisions (all locked with Boss, S356)

### 1. Dashboard-first structure

- **Progress goes LAST.** Everything above it is the dashboard.
- **Dashboard is self-sufficient for present-time action.** A general reads top-down and has everything needed to keep pushing before reaching Progress.
- **Progress is load-bearing for archaeology / debrief / onboarding** — just not on the critical path for "what do I do now?"

### 2. Sections = memory types (architectural, not metaphorical)

| Widget | Memory type | Discipline | Grows? |
|---|---|---|---|
| **Identity** (Telos/Charter/Victory Conditions) | Identity | Near-immutable. Changes only by deliberate reframe. | No |
| **Matrix** | Structural ledger | Rows append-only; cells update to final state; NEVER delete rows | Yes, bounded by children spawned |
| **Situation** | Episodic | Rewritten each session; LIVE items only (🔵/🟡/⏳); closed items drop off | Bounded (session-cap) |
| **Intel** | Semantic | Present-tense doctrine; curated; NO chronology; NO session provenance; origin-links on promoted entries | Slow, bounded by scope |
| **Progress** (last) | Autobiographical | Append-only narrative; linked mentions; rounds as chapters | Unbounded (the story) |

**Prospective memory = IMPLICIT in child existence** (fractal). A quest's missions ARE the quest's commitments to act. No separate prospective section — the filesystem topology carries it.

**Two accreting widgets:** Matrix (row-per-child) + Progress (session-narrative). Dashboard stays O(1) per session because only Progress grows in a skippable way.

### 3. Intel model — flat + level-encoded

- **Flat list** of present-tense truth-statements at this scope.
- **Classification encoded by FILE LEVEL** — not by tags inside files. Mission Intel = tactical-by-residence. Quest Intel = operational. Campaign = strategic. Warroom = doctrinal.
- **No classification tags** inside Intel (🔬/⚙️/♟️/📜 retire as in-band markers).
- **No S-numbers, no chronology.**
- **Promotion = relocation + origin-link.** A tactical finding maturing into operational MOVES to the quest file (rewritten in operational voice), with a backlink to origin.
- **One intel, one home.** Zero duplication.
- **Salience markers** (🔴 critical, 🎯 turning-point) orthogonal — used sparingly to flag emphasis.

### 4. Glyph vocabulary

**STATES (closed enum — traffic-light circles + check/X):**
- 🔴 BLOCKED · 🟡 REVEALED · 🔵 ACTIVE · ✅ COMPLETE · ❌ FAILED · ⚫ ABANDONED

**ACTIONS (OPEN vocabulary; conventional glyphs for stack-op categories):**

Actions are function calls — verb vocabulary is open, not enumerated. The cooperative-execution model requires fixed SEMANTIC CATEGORIES; the verbs authors reach for flow with the work.

| Category | Conventional glyph | Natural verbs |
|---|---|---|
| Dispatch | ➕ | forged, spawned, created, commissioned, briefed |
| Round-start | ▶️ | engaged, opened, began, kicked-off |
| Round-yield | ◀️ | landed, yielded, returned |
| Await | ⏳ | awaiting, waiting, blocked-on |
| Decision | ◆ | decided, chose, committed |
| Return-complete | ✅ | completed, shipped, delivered |
| Return-failed | ❌ | failed, errored |
| Return-abandoned | ⚫ | abandoned, cancelled, dropped |

Beyond stack-ops, open vocabulary for richer timeline events (investigated, discovered, reframed, pivoted, validated, rejected, escalated, deferred, merged, split…). Glyphs for those are case-by-case, picked by semantic family (red=problem, green=good, 🔍 investigation, 💡 insight, etc.) or skipped when prose carries it.

**RETIRES:** ⚒️ hammer-and-pick · 🪂 parachute · ⚡ lightning · 🏆 trophy · 💀 skull · 🏳️ flag · 🗺️ map · ⚔️ swords · 🔬 microscope · ♟️ chess pawn · 📜 scroll · 🌫️ fog · ☀️ sun.

**SALIENCE (minimal):** 🔴 critical · 🎯 turning-point. Used where warranted, not everywhere.

**FOG ZONES:** retire as dashboard widget (⬛/🌫️/☀️ go). Keep as **planning discipline** in prose — "plan only what fog has revealed" remains the governing principle.

**CLASSIFICATION TAGS:** retire. Level IS classification.

### 5. Linking discipline — Obsidian-vault energy

**Every cross-file reference is a link.** The warroom is a knowledge graph, not a folder hierarchy.

- **Tree** for composition (warroom/campaign/quest/mission)
- **Graph overlays** for data flow (promoted intel with provenance, cross-pollination between siblings, external prior-art pointers)
- **Promotion carries origin-link** — the "foreign key" pattern. `[Origin: q04/m01](...)` at the destination.
- **Every claim with provenance carries its pointer** — readers never guess where something lives.
- **Matrix rows** link to child file/place. **Situation entries** link to the live item. **Progress mentions** of other missions/quests always link.

### 6. Actions grammar (unchanged)

Blockquote syntax: `> **verb** \`object\` — prose context`. The glyph earns its place by scan-value; no glyph-by-obligation. Stack-op categories get conventional glyphs because they appear often; novel verbs pick glyphs by semantic family or skip.

---

## Derivable in the draft (not explicitly probed)

### Mission file shape

Identity (Charter) → Success Criteria → Deliverables → Intel → Progress (last, rounds as narrative chapters inside). No Matrix (mission has no child files — rounds live IN Progress). No Situation (the mission itself IS the current focus; Deliverables + open rounds carry what's-hot).

### Matrix column design

State glyph EARLY for scan priority. Candidate: `| ## | State | Name | Goal |`. "Outcome" column folds into State — the final state glyph (✅/❌/⚫) IS the outcome.

### Situation widget form

Bulleted list of linked live items with current state + brief note. One line per item. Rewritten each session. Only 🔵 ACTIVE / 🟡 REVEALED / ⏳ awaiting items appear. Closed items drop off (they persist in Matrix + Progress).

Example shape:
```markdown
## Situation
- 🔵 [m02 lib/benstack scaffold](m02-scaffold.md) — r1 engaged, Rust crate up
- 🟡 [m03 wifi bridge](m03-wifi-bridge.md) — revealed, awaiting m02 landing
- ⏳ [D2 ben exec decision](../workshop/d2-memo.md) — awaiting Boss authority
```

### Prior Art / References widget

At warroom + campaign levels — an explicit link-list widget. Static pointers to authoritative external artifacts (governing frames, spec documents, upstream dependencies). Separates "what to read to orient" from "what is currently true."

---

## Relationship to BentOS vision

- QuestForge is a **flagship LApp for the BentOS Linux distro pre-install catalog**. A consumer-facing Linux distro is as cool as what comes pre-installed.
- Today's body: `.claude/skills/quest-forge.app/` atom + markdown conventions.
- Future body: `quest-forge.exe` — Flutter widgets, Agentic HUD integration, Agent Core (Dungeon Master), manifest + capabilities.
- **RPG vocabulary is the methodology, not decoration.** Same vocabulary, richer rendering across platform evolution.
- The atom's conceptual shape SURVIVES the platform journey — that's why getting the spec right now matters.

---

## Rewrite plan

1. **README.md rewrite** — full pass, single artifact, total focus. This is the doctrine.
2. **atom.xml mechanical re-derivation** — agent-loaded substrate aligned to the README.
3. **c04 warroom v2.0 retrofit** — dogfood the updated methodology on current warroom state. Separate session.

**Cadence:** full pass, then critique.

---

## The smells dissolved this session

- Glyphs picked by Unicode-keyword match (teenage dungeon-master costume).
- "Key Discoveries" as chronological log (duplicating Progress).
- Closed set of 8 action verbs (procrustean).
- Matrix-as-episodic (wrong — it's structural ledger).
- Classification tags in-band (level IS classification).
- "Documents that grow" without memory-type discipline (no curation rules per section).

---

*S356. Design dialogue: Cafe + Alfred. Next beat: README rewrite, full pass.*
