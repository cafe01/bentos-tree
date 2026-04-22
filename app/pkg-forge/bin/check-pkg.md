---
name: check-pkg
description: Verify atom health - examine, diagnose, and heal living software packages
disable-model-invocation: true
---

Execute the **check-pkg protocol** — examine and heal the health of living atoms.

Requires `pkg-forge.app` in working memory. If not present, stop and ask the user to invoke `/pkg-forge.app` first. Otherwise, execute `<protocol name="check-pkg">`.

Scope from invocation: `$ARGUMENTS` (all, a family, or a specific atom path).
