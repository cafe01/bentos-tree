# QuestForge atom v2.0 — convergence notes

**Session:** S356
**Channel:** alfred-forge-s356 (alfred root + alfred-forge-01 head)
**Purpose:** Institutional record of the living-abstract design debate — the reasoning behind the ten invariants, so future agents debugging drift have more than the outcome.

---

## The load-bearing reframe that shaped the debate

Boss: *"The living-abstract itself must be designed at product-spec (README.md) level. That's the bridge from product (spec) to implementation (concrete atom.xml)."*

This recontextualized the forging. The living-abstract is not an atom section filled in after the README — it's the **soul of the product expressed in atom syntax**, at the same design quality as the README. README and abstract are **coherent siblings**: one in product-spec prose, one in atom vocabulary, both load-bearing.

The "bridge test" followed from this frame: if the README treats something as load-bearing invariant, the abstract gives it a principle. If the README treats something as architectural consequence, it's concrete-territory.

---

## Round 1 — session-manager scaffold, head's independent read

Session manager ("team-lead") seeded a scaffold with 4 capacities + 7 principles and explicit probes on 5 uncertainties. Head ("alfred-forge-01") wrote an independent pass from scratch, then diffed.

### Essence — reframed

**Scaffold:** *"Living Application that turns complex endeavors into legible warrooms — situation room above, living story below."*

**Head's pass:** *"Warroom discipline — fractal living stories with a cooperative-execution model. Situation room above, living story below."*

**Converged to head's version.**

Reasoning: "Living Application" is TRUE but it's a fact about substrate trajectory, not platonic essence. Linux distro analogy: a distro is a "Living OS" but its essence isn't that — its essence is "a Unix-family operating system." Same logic. The README's own subtitle nails the essence; abstract's essence should ~= README subtitle. LApp framing demoted to concrete knowledge as `living-application-trajectory` — metadata about substrate, not methodology axiom.

### Purpose — tightened

**Scaffold:** *"Equip organisms to run fractal async work without losing the plot — dashboards for present action, cooperative-execution vocabulary for coordination, living stories for institutional memory"*

**Head's pass:** *"Make serious multi-session work legible, finishable, and honest — by giving async execution vocabulary and turning the filesystem into a navigable call stack."*

**Converged to head's version.**

Two moves: "legible, finishable, honest" is the triad QuestForge actually delivers (legibility = dashboards, finishability = victory conditions + three return modes, honesty = FAILED/ABANDONED as first-class). "Navigable call stack" crystallizes the deepest v2.0 insight — filesystem IS the stack trace. "Institutional memory" from scaffold is covered by "honest" (honesty includes not deleting Progress to clean up).

### Capacities — four different axes

**Scaffold:** compose, dashboard, orchestrate, curate
**Head:** structure, dashboard, execute, navigate
**Converged to head's version.**

Key moves:
- **`navigate` elevated to capacity.** Reading a warroom is a distinct skill from writing one (following ⏳ down, propagating ✅/❌/⚫ up). v1.0 had it as a protocol; v2.0 promotes because the HUD/Visualizer on the roadmap IS navigate rendered as native widget. Execute = writing the stack; navigate = reading it.
- **`curate` folded into `dashboard`.** Curation IS the dashboard's memory-type contract — splitting weakens both. `dashboard` capacity + `memory-type-per-widget` principle together carry the full weight.
- **`structure` beats `compose`.** Compose is generic; structure anchors to THE fractal. Name should make a reader think "ah, THE fractal" not "composing what?"
- **`execute` beats `orchestrate`.** Orchestrate connotes top-down control; execute matches the actual functional/async model. Words matter.

### Principles — the five disagreements

1. **`living-application` — PRINCIPLE or FACT?** Head argued fact. Test: can you describe the atom without invoking it? Yes — QuestForge works today for humans on raw markdown with zero LApp infrastructure. The LApp framing is metadata about trajectory, not an invariant the methodology rests on. **Resolution: dropped from principles, added as `living-application-trajectory` knowledge in concrete.**

2. **`three-return-modes` — KEEP or CUT?** Scaffold cut it. Head argued keep: not derivable from cooperative-execution (you could have cooperative execution with only ✅/❌). ⚫ ABANDONED is a SEPARATE invariant — garbage-collected returns are first-class; permanent projects are the antipattern this kills. Bridge-test: README dedicates a section to it. **Resolution: principle, with wording "Complete, failed, abandoned — all first-class. Honest tracking requires naming giving up."**

3. **`interactive-execution` — PRINCIPLE or CONCRETE?** Scaffold called it concrete. Head argued principle: without it, `execute` capacity collapses into dispatch-and-wait. Fire-and-forget rounds violate the cooperative-execution model at the mission level. Cooperative-execution names the functional model; interactive-execution names the comms discipline during execution — they govern different things. **Resolution: principle, with wording "Troops in comms with their general. Attunement before engagement. The Pentagon does not cut radio contact."**

4. **`visual-semantics` — PRINCIPLE or CONCRETE RULE?** Scaffold called it concrete. Head argued principle via functional test: "if an author picks ⚒️ for dispatch (Unicode-keyword match), what do you cite to reject it?" The visual-semantics principle. That's what principles DO — they govern choices. Bridge-test: README dedicates a whole section to it. **Resolution: principle, with wording "Glyphs are the icon font. Every glyph passes the 16×16 UI test. Emoji IS the value."**

5. **Attracts — ONE or TWO?** Scaffold proposed `content-direction.structuring.craft.skill` alone. Head proposed both + `first-principles.cognition.meta.skill`. Fog-of-war + "questions from walls" IS first-principles discipline applied to planning — the meta-skill that prevents mission-as-exploration drift. **Resolution: both.**

---

## Round 2 — bridge-test refinement (`work-at-target` as #10)

Session manager surfaced a final probe: `work-at-target`. README has the prohibition distributed across three places but no dedicated top-level heading. Scaffold's lean: keep as antipattern only (`warroom-as-filing-cabinet`), cite nothing.

Head pushed back with three arguments:

1. **Bridge-test refinement.** The test isn't "does README have a `##` heading?" — it's "does README treat it as load-bearing invariant?" The invariant appears in three README places including the strongest rhetorical form the README uses: identity-level negation in "What it is NOT" ("Not a filing system. The warroom is mission control, not a cabinet of archived projects"). Same weight as "Not a TODO app" and "Not gamification."

2. **Functional coverage.** Nothing else in the abstract prevents dumping a Rust crate inside `c04-benstack/q02/m02/deliverables/`. `dashboard-first` governs file internals; `fractal-self-similarity` governs structural recursion; `memory-type-per-widget` governs section curation; `one-intel-one-home` governs knowledge dedup. Filesystem topology of work product has no home without this principle.

3. **Antipattern-needs-anchor.** `warroom-as-filing-cabinet` antipattern wants to cite something. Without `work-at-target` as principle, the prohibition floats unanchored.

**Resolution: principle #10, wording "Deliverables live where they're consumed. The warroom tracks; it doesn't store. Mission control, not filing cabinet."** Placed adjacent to `one-intel-one-home` — pair reads as "locations invariants" (intel lives at one level; deliverables live at target).

Session manager conceded on merit: "Bridge-test refinement — distributed-across-three-places IS load-bearing. I applied the heuristic too literally; section-gated isn't the real criterion, rhetorical weight is."

---

## The locked ten — ordering tells a story

Concerns flow: **structure → curation → execution → planning → location → rendering.**

| # | Principle | Concern |
|---|---|---|
| 1 | dashboard-first | structure |
| 2 | fractal-self-similarity | structure |
| 3 | memory-type-per-widget | curation |
| 4 | cooperative-execution | execution |
| 5 | three-return-modes | execution |
| 6 | interactive-execution | execution |
| 7 | fog-of-war | planning |
| 8 | one-intel-one-home | location |
| 9 | work-at-target | location |
| 10 | visual-semantics | rendering |

The ordering is itself a teaching artifact — a reader scanning the principles picks up the shape of the discipline in order.

---

## Cut explicitly (so they don't re-litigate)

- **`open-verb-vocabulary`** — implementation detail of cooperative-execution. Lives in concrete as `actions` knowledge + `procrustean-closed-verbs` antipattern.
- **`classification-by-level`** — implementation detail of one-intel-one-home. Lives in concrete as `intel-flow` knowledge + `in-band-classification-tags` antipattern.
- **`narrative-as-methodology`** — philosophical commentary, not invariant. The RPG frame shapes thought but doesn't govern choices the way principles must. Retired as explicit principle; its spirit lives in the "What it is NOT → Not gamification" section of the README.
- **`lean-dashboard`** — descriptive consequence of `memory-type-per-widget` (Situation's curation discipline), not separate invariant.
- **`navigation-is-ux`** — descriptive consequence of `one-intel-one-home` + the graph-overlays model. Belongs in concrete `linking-as-ux` knowledge, not as standalone principle.
- **`O(1)-dashboard`** — a scaling-law observation flowing from memory-type discipline, not invariant.

Each cut had a reason. Record here so we don't reconsider on vibes.

---

## README sharpening convergence

After abstract lock, head proposed aligning README's "Design commitments" section 1:1 to the abstract's 10 principles — same names, same order, same groupings (structure/curation/execution/planning/location/rendering). Session manager agreed; executed in Phase 1 of this session's delivery.

The old 20-item Design commitments list compressed into 10 entries named to match the abstract. Items that were cut-from-abstract (living-application, open-verb-vocabulary, classification-by-level, lean-dashboard, navigation-is-ux, narrative-as-methodology, O(1)-dashboard, living-stories) either folded into their parent principle's scope or retired entirely — their spirit preserved in the prose of earlier README sections.

Result: README ↔ abstract sibling relationship is now VISIBLE. A reader who sees "dashboard-first" in the abstract finds it both in Design commitments and as a `##`-level section elaboration earlier. Both artifacts co-evolve going forward.

---

## What comes next

- c04 warroom (and others) need retrofit to v2.0 — separate session, dogfood the methodology.
- The atom's concrete may accrete protocols or knowledge as v2.0 lives; the abstract should stay stable absent a new paradigm-level reframe.
- Future versions: evolve through friction, not speculation. Same discipline this session's debate exemplified.

---

*S356. Design dialogue: Cafe (Boss) + Alfred session-manager + Alfred-forge-01 head. Next beat: install, verify, commit, ship.*
