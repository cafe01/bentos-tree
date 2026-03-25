# Plasticity Nap — S307 alfred-plasticity-01

## Completed

### 1. Embodiment v17 -> v18: Kill "Active Main"
Three-tier thread model (session manager / active main / other heads) collapsed to two-tier:
- **SESSION MANAGER** ({agent}-session): main thread, lifecycle only. No incarnation suffix.
- **HEADS** ({agent}-{purpose-domain}-{incarnation}): all purpose-domain scoped. No special "main" type.

Infection sites cleaned: thread-model knowledge, thread-lifecycle, hydra-growth diagram,
Claude Code shim vocabulary-mapping, session-main-conflation antipattern (removed — concept extinct).

### 2. Anamnesis v16 -> v17: Terminology fix
"Main thread" labels in wake/sleep protocols replaced with "session manager" where
they referred to {agent}-session. "HEAD THREAD" shortened to "HEAD".

### 3. Hook frontmatter fix (from alfred-coo-01)
Nested `hooks:` key in organism frontmatter was wrong. Fixed in both
`assemble_command.dart:212` and `organism_assembler.dart:368`.
Note: DRY violation — two separate `_buildFrontmatter` implementations exist
(CLI command + assembler). Command's version is the one actually used by `forge organism`.

### 4. All organisms re-forged
`forge organism '*.soul'` — 4 agents rebuilt with both fixes.

## Committed
- bentos-tree submodule: `449beac` — evolve(faculty)
- bentos_agent submodule: `ef578b9` — fix(forge)
- superproject: `9c59528` — evolve(S307)

## Open observations
- The assembler's `_buildOrganism` / `_buildFrontmatter` is dead code for the `forge organism` path.
  The CLI command bypasses it entirely. Consider consolidating.
- S306 evolve-nap.md at root .mem is now stale — this nap supersedes it for plasticity context.
