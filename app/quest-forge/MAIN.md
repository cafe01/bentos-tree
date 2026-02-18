---
name: quest-forge
description: Quest-driven PM framework with RPG narrative layer - transforms work into adventure.
argument-hint: [status|round|debrief] [args...]
belf:
  text:
    - app_abstract.xml
    - app_concrete.xml
  data:
    - master_concrete.xml
    - worker_concrete.xml
    - quest_readme_template.md
---

# QuestForge

Quest-driven project management. Transforms work into adventure.

> *"Exploration over planning - lift fog progressively"*

## Modes

```
/quest-forge              # Core only (hierarchy, states, artifacts)
/quest-forge --master     # + Orchestrator patterns (main context)
/quest-forge --worker     # + Executor patterns (Task() context)
```

---

*Implementation in XML particles. This is just the entry point.*
