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

Every package contains an `atom.xml` entry point with a BELF header (BentOS ELF — the package manifest). The header declares which files to load:

- **text** (static-linked): Always loaded on install. The program itself.
- **data** (dynamic-linked): Loaded on demand at runtime.

Typical package contents:

```
soul/alfred/
  atom.xml              # Entry point + BELF header
  soul_abstract.xml     # Immutable ideal (what this soul aspires to)
  soul_concrete.xml     # Mutable reality (current state, evolves)
  MAIN.md               # Platform-specific install artifact
```

## Install Model

Packages compile on install to platform-native artifacts. On Claude Code, this means generating skill directories:

```
bentos-agent install alfred.soul
# Compiles: soul/alfred/ -> .claude/skills/alfred.soul/SKILL.md
```

The source tree is text. The install artifact is platform-specific. Same source, different targets — like ports compiling C to different architectures.

## The Periodic Table

The `schema/` directory defines the **periodic table of BentOS** — the structural model that constrains what packages can exist. Skills are positioned along five axes (Craft, Discipline, Domain, Tools, Meta). Atoms belong to families (Soul, Faculty, Skill, App, Genesis). The table is bounded: it grows through discovery of genuine capability needs, not through arbitrary proliferation.

This bounded composition is what separates a ports tree from npm. The periodic table is the constitution; the tree is the territory it governs.

## Contributing

Packages in this tree are living software. They improve through the `evolve` protocol: use a package, encounter friction, propose an evidence-based improvement. Every evolution traces to real experience, not theory.

## License

MIT. See [LICENSE](LICENSE).
