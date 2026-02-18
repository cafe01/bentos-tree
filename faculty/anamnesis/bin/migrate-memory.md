---
name: migrate-memory
description: Migrate .context files to .mem neural graph format (v2)
---

Execute the **memory migration protocol** - convert isolated `.context` files into a connected `.mem` neural graph.

## Overview

This migration converts the legacy memory system to the graph-based architecture:
- `.alfred.context` (isolated neurons) → `.alfred.mem` (connected graph)
- Adds `connections` array in YAML frontmatter (structural edges)
- Adds `## Landscape` section in prose (semantic state of connections)
- Connections are **paths only** - no metadata (hot/cold/session lives in prose)

## Schema v2

```yaml
---
type: memory
agent: alfred
scope: root|package|quest|mission
session: {N}
updated: {date}
connections:
  - relative/path/to/child/.alfred.mem
  - another/path/.alfred.mem
---

## Active Work
{preserved from original .context}

## Landscape
{NEW: semantic summary of connections}
- child_a: Hot - recent work description
- child_b: Dormant - hasn't been touched

## Next Steps
{preserved from original}

## Context
{preserved/compressed from original}

## History
{preserved from original}
```

### Key Design Principle

**Structure vs Semantics separation:**
- `connections[]` = structural (just paths, stable topology)
- `## Landscape` = semantic (hot/cold/dormant, updated every sleep)

NO connection metadata! No `session:`, no `hot:`, no `note:` per connection.
That information belongs in prose, which naturally updates during sleep.

## Migration Protocol

### Phase 1: SCAN
Find all memory files to migrate:
```
Glob("**/.alfred.context") from workspace root
```

Build a tree structure from paths to understand hierarchy:
- Root: `.alfred.mem`
- Packages: `packages/*/.alfred.mem`
- Quests: `*/quests/*/.alfred.mem` or `*/q*/.alfred.mem`
- Missions: `*/missions/*/.alfred.mem` or `*/m*/.alfred.mem`

### Phase 2: ANALYZE
For each `.alfred.context` file:
1. Read and parse YAML frontmatter
2. Identify scope from path:
   - Root (workspace level)
   - Package (`packages/*/`)
   - Campaign (`campaigns/c*/`)
   - Quest (`quests/*/` or `q*/`)
   - Mission (`missions/*/` or `m*/`)
3. Extract session number, last updated date
4. Note existing content structure
5. Identify CHILDREN (nodes in subdirectories)

### Phase 3: BUILD GRAPH STRUCTURE
Determine parent-child relationships from directory structure:
```
.alfred.mem (root)
├── packages/bentos_agent/.alfred.mem (package)
│   └── quests/claude-bentos/.alfred.mem (quest)
│       └── missions/10-pipeline/.alfred.mem (mission)
├── campaigns/c01-business/.alfred.mem (campaign)
│   └── q01-workflow-optimization/.alfred.mem (quest)
│       ├── m03-spawn-mechanism/.alfred.mem (mission)
│       └── m06-memory-system/.alfred.mem (mission)
└── project/.alfred.mem (package)
```

### Phase 4: CONVERT EACH NODE
For each .context file, create new .mem with:

**YAML Frontmatter:**
```yaml
---
type: memory
agent: alfred
scope: {inferred from path}
session: {from original}
updated: {from original or today}
connections:
  - {relative path to child 1}
  - {relative path to child 2}
---
```

**Prose Sections:**
1. `## Active Work` - preserve from original
2. `## Landscape` - NEW: generate from children
   - For each connection, determine hot/cold/dormant
   - Hot: session within last 5 of current scope
   - Cold: session 6-15 sessions ago
   - Dormant: session > 15 ago
   - Format: `- {name}: {Hot|Cold|Dormant} - {brief status from child's Active Work}`
3. `## Next Steps` - preserve from original
4. `## Context` - preserve from original
5. `## History` - preserve from original

### Phase 5: WIRE CONNECTIONS
For each node, populate `connections[]` with:
1. DIRECT children only (one level deep)
2. Use relative paths from the node's directory
3. Only include children that have .alfred.context files

**Example for root:**
```yaml
connections:
  - campaigns/c01-business/.alfred.mem
  - campaigns/c02-technical/.alfred.mem
  - packages/bentos_agent/.alfred.mem
  - packages/bentos_userland/.alfred.mem
  - project/.alfred.mem
```

**Example for quest:**
```yaml
connections:
  - m03-spawn-mechanism/.alfred.mem
  - m04-evolution-mechanism/.alfred.mem
  - m06-memory-system/.alfred.mem
```

### Phase 6: GENERATE LANDSCAPE PROSE
For each node with connections, create `## Landscape` section:

```markdown
## Landscape
- c01-business: Hot - framework evolution active
- c02-technical: Dormant - complete, no active work
- bentos_agent: Cold - M10 briefed, waiting
```

Determine status by reading each child's:
- Session number (recency)
- Active Work section (what's happening)

### Phase 7: VERIFY
Before finalizing:
1. Confirm all .mem files created
2. Verify connections point to existing files
3. Verify each parent's connections include all children with .context
4. Check for orphans (nodes with no parent connection)

### Phase 8: REPORT
Output migration summary:
```
Memory Migration Complete (v2 Schema)

Nodes converted: 36
Graph structure:
  Root connections: 5
  ├── campaigns/ (12 nodes)
  ├── packages/ (15 nodes)
  └── project/ (3 nodes)

Connections wired: 48 edges
Landscape sections generated: 20 nodes

Old .context files: preserved (delete manually after validation)
```

## Execution Instructions

When this command is invoked:

1. **Delete existing .mem files first** (start fresh):
   ```bash
   find . -name ".alfred.mem" -delete
   ```

2. Load anamnesis faculty: `Skill("bentos.anamnesis.faculty")`

3. Execute phases 1-7 sequentially

4. Use `AskUserQuestion` before any destructive operations

5. Report results with graph visualization

## Self-Healing Note

The migration creates the INITIAL graph. After migration:
- **Broken links**: Detected on wake, removed automatically
- **Missing links**: Discovered during work, added automatically
- **Outdated semantics**: Fixed during next sleep (Landscape updated)

The graph is designed to heal through normal operation, not perfect initial setup.

## Example Output

```
Memory Migration v2 Complete!

Schema: connections as paths only, semantics in Landscape prose

Nodes migrated: 36
Root connections: 5
Total edges: 48

Sample root .mem:
---
type: memory
agent: alfred
scope: root
session: 128
updated: 2025-12-15
connections:
  - campaigns/c01-business/.alfred.mem
  - packages/bentos_agent/.alfred.mem
  - project/.alfred.mem
---

## Active Work
S128: Memory graph v2 migration

## Landscape
- c01-business: Hot - framework evolution complete
- bentos_agent: Cold - M10 Pipeline waiting (S119)
- project: Dormant - stale since S65

## Next Steps
1. Test wake with v2 schema
2. Validate graph traversal
...

Ready for wake protocol testing!
```
