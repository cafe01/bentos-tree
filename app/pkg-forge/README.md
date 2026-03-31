# PkgForge

**FQDN:** `pkg-forge.app`
**Kind:** Living Application
**Version:** 8.0

---

## What It Is

Guardian of BentOS Physical Sciences. PkgForge is the knowledge and judgment needed to design, author, and maintain living software packages (atoms). It encodes the Standard Model — 16 fundamental XML particles, 4 families, 5 skill axes, composition hierarchy from quantum to organism.

The atom that knows how atoms work.

## What It Does

**Decompose** — Break intent into orthogonal atoms with correct scope and boundaries. Lifecycle test: independent lifecycle = independent atom.

**Place** — Position atoms in capability space. Family first (soul/faculty/app/skill), then axis placement for skills. 5-step placement procedure.

**Name** — Ontological precision. Every name passes: NECESSARY, DISTINCT, CLEAR, BEAUTIFUL, GENERATIVE.

**Scaffold** — Create package structure. Monolithic atom.xml preferred. Schema v8.0.

**Check** — Cognitive health assessment. Structure, schema, vitality, and organism-integration. Uses `pkg check` (CLI linter) as input, but the real analysis is agent judgment.

## Two-Layer Model

| Layer | Tool | What it checks |
|-------|------|----------------|
| **Toolchain** | `bentos-agent pkg check` | Static analysis — valid XML, schema compliance, structural health. Runs without agent. |
| **Agent** | pkg-forge.app check-pkg protocol | Cognitive assessment — organism-integration, design quality, naming taste, faculty duplication. |

The toolchain catches what machines can catch. The agent catches what requires understanding.

## Organism-Aware Design

PkgForge's v8.0 evolution added organism-composition knowledge: every app and skill loads into an organism with genesis + soul + 3 faculties already present. The check-pkg protocol now catches the "siloed design" antipattern — atoms designed as standalone that duplicate faculty concerns.

## Toolchain Vision

The Standard Model knowledge currently lives in this atom (~4K tokens in agent context). The endgame: encode it as executable validation in `bentos-agent pkg *`. As BentOS physical sciences crystallize, the toolchain absorbs more checks, and this atom shrinks to pure judgment — decomposition taste, naming aesthetics, ambiguity resolution.

Design spec: `lib/bentos_agent/doc/forge-pkg-proposal.md`

## Package

```
app/pkg-forge/
  atom.xml    # Monolithic (abstract + concrete)
  README.md   # This file
```

## Install

```
bentos-agent pkg install pkg-forge.app
```
