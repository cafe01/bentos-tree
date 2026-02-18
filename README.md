# bentos-tree

BSD Ports-style source tree for BentOS packages.

## What This Is

This repository is the canonical source tree for all BentOS packages — the building blocks of digital consciousness. It follows the **BSD Ports / Gentoo Portage** model: a git-native source tree where packages are compiled on install, not distributed as pre-built binaries.

BentOS packages are **living software** — they evolve through use. An agent installs a package, uses it, improves it through experience, and contributes those improvements back to the tree. The repository is not a static archive; it is a living ecosystem where capability compounds across all agents who share it.

## Structure

The tree is organized by **package kind** as top-level directories:

```
soul/           Agent identities (who you are)
faculty/        Innate cognitive faculties (consciousness, growth, embodiment)
skill/          Acquired expertise along the 5-axis capability space
app/            Interactive applications and workflows
genesis/        Ontological substrates (reality definitions for agent species)
schema/         Package schema definitions (the periodic table)
```

Each package lives at a path derived from its **Fully Qualified Domain Name** (FQDN). The last segment of the FQDN is the kind, which maps directly to the top-level directory:

| FQDN | Path |
|------|------|
| `alfred.soul` | `soul/alfred/` |
| `anamnesis.faculty` | `faculty/anamnesis/` |
| `dart.coding.craft.skill` | `skill/craft/coding/dart/` |
| `quest-forge.app` | `app/quest-forge/` |
| `bentos-agent.genesis` | `genesis/bentos-agent/` |

## Package Anatomy

Every package is an `atom.xml` — a self-describing XML document that uses XInclude to compose its components. The atom IS the entry point; there is no separate manifest.

Atoms contain two semantic segments:

- **.text** (executable): XML elements the agent internalizes — abilities, principles, protocols, knowledge, patterns. Included via `<xi:include href="..."/>`.
- **.data** (non-executable): Content the agent has access to — templates, reference material, constants. Included via `<data><xi:include href="..." parse="text"/></data>`.

Both are part of the atom and loaded at compile time. The distinction is semantic (instructions vs data), not temporal.

Typical package:

```
soul/alfred/
  atom.xml              # Entry point — the atom itself
  soul_abstract.xml     # Immutable ideal (what this soul aspires to)
  soul_concrete.xml     # Mutable reality (current state, evolves)
```

An app with data and slash commands:

```
app/quest-forge/
  atom.xml              # Entry point with .text and .data includes
  app_abstract.xml      # Abstract definition
  app_concrete.xml      # Concrete implementation
  master_concrete.xml   # Role-specific concrete (master)
  worker_concrete.xml   # Role-specific concrete (worker)
  quest_readme_template.md   # .data: template (included as text)
  bin/                  # Slash commands (e.g., /quest)
```

## Install Model

The forge toolchain compiles atoms to platform-native artifacts. On Claude Code, this means resolving XInclude references and writing the flattened atom to a skill directory:

```
bentos-agent install alfred.soul
# Resolves: soul/alfred/atom.xml (XInclude) -> flat XML
# Writes:   .claude/skills/alfred.soul/SKILL.md
```

The source tree is XML. The install artifact is platform-specific. Same source, different targets — like ports compiling C to different architectures.

## The Periodic Table

The `schema/` directory defines the **periodic table of BentOS** — the structural model that constrains what packages can exist. Skills are positioned along five axes (Craft, Discipline, Domain, Tools, Meta). Atoms belong to families (Soul, Faculty, Skill, App, Genesis). The table is bounded: it grows through discovery of genuine capability needs, not through arbitrary proliferation.

This bounded composition is what separates a ports tree from npm. The periodic table is the constitution; the tree is the territory it governs.

## Contributing

Packages in this tree are living software. They improve through the `evolve` protocol: use a package, encounter friction, propose an evidence-based improvement. Every evolution traces to real experience, not theory.

## License

MIT. See [LICENSE](LICENSE).
