# Feature Request: Pocket Edition Generation

**Status**: PROPOSED
**Requested**: S180 (refined S181)
**Requester**: Boss + Alfred

---

## Problem

Books are canonical sources of knowledge. However:

1. **Context blow-up**: Loading multiple books exceeds agent RAM
2. **Degraded cognition**: >60% context usage = degraded reasoning
3. **Re-work**: Each consumer re-reads and re-summarizes

**RAM is finite** - for LLMs AND humans. This is physics, not preference.

---

## Concept: Pocket Edition

A pocket edition is a **compressed representation of a book optimized for context loading**.

```
pocket_edition = book.essence() + book.structure() + book.navigation()
```

| Component | What It Is |
|-----------|------------|
| **essence** | The irreducible core that makes this book THIS book |
| **structure** | How the book is organized (chapters, flow) |
| **navigation** | Pointers to full content when depth is needed |

### What a Pocket Edition IS

- **Self-contained**: Readable and useful without the original
- **Structural**: Preserves book organization, not just content
- **Navigable**: Points to full content when depth needed
- **Genre-aware**: Compression strategy adapts to book type

### What a Pocket Edition IS NOT

- **Not a summary**: Summaries lose structure
- **Not an abridgement**: Abridgements cut chapters wholesale
- **Not interpretation**: Pocket preserves, doesn't analyze

---

## Genre-Awareness

The core principle is universal: **preserve essence, compress elaboration**.

But what counts as "essence" vs "elaboration" is genre-dependent:

| Book Type | Essence | Elaboration |
|-----------|---------|-------------|
| Technical doc | Concepts, specs, definitions | Examples, walkthroughs |
| Novel | Plot, characters, themes | Scene details, dialogue |
| Philosophy | Arguments, positions | Rhetorical flourishes |
| Poetry | The poems themselves | Commentary, analysis |
| Reference | Definitions, relationships | Extended explanations |
| Tutorial | Steps, outcomes | Detailed instructions |

The LLM executing the command IS the compression algorithm. It reads the book, infers genre, applies judgment.

---

## Interface

```
/bentos:books:gen-pocket-edition ./books/ontology/
```

### Arguments

| Arg | Required | Description |
|-----|----------|-------------|
| `path` | Yes | Path to book directory |

### Output

Single `README.pocket.md` file written to book root (visible, discoverable, alongside README.md).

---

## Principles

1. **Genre-awareness**: Infer book type, adapt compression strategy
2. **Structure preservation**: Chapter organization maintained
3. **Essence extraction**: What makes this book THIS book
4. **Navigability**: Links/references to original for deep dives
5. **Token efficiency**: Target ~20% of original (heuristic, not rule)

---

## Quality Criteria

A good pocket edition enables the reader to:

- [ ] Understand the book's scope and purpose
- [ ] Reference specific concepts by name
- [ ] Know the book's structure and flow
- [ ] Identify WHEN to consult the full version
- [ ] Load multiple pocket editions simultaneously

---

## Use Cases

1. **Multi-book reasoning**: Load 5 pocket editions instead of 1 full book
2. **Onboarding**: Quick orientation before deep-dive
3. **Cross-reference**: Compare concepts across books
4. **External tools**: Optimized input for NotebookLM, etc.

---

## Implementation Notes

### Architecture: Interface + Implementation Split

This feature uses a **token optimization pattern**:

| Layer | Location | Loaded | Contains |
|-------|----------|--------|----------|
| Interface | `app_abstract.xml` | Always (with app) | Ability declaration |
| Implementation | `bin/gen-pocket-edition.md` | On-demand (when invoked) | Heavy business logic |

**Why split?**
- Abstract stays lean (ability exists, ~1 line)
- Implementation loaded only when command runs
- RAM-efficient: don't pay for what you don't use

### Files to Modify

1. **`app_abstract.xml`**: Add ability declaration
   ```xml
   <ability name="compress">Generate pocket edition - compressed book for context loading</ability>
   ```

2. **`bin/gen-pocket-edition.md`**: Full implementation (this feature request becomes the basis)

### Algorithm (conceptual)

1. **Detect**: Validate directory is a book
2. **Infer**: Determine genre/purpose from content
3. **Extract**: Per-chapter essence (genre-aware)
4. **Consolidate**: Glossary, cross-references
5. **Generate**: Write `.pocket.md`

### NOT Specified (deliberately)

- Exact output format (let implementation decide)
- Compression ratios per content type
- Genre-specific extraction rules

These are implementation details. The LLM applies judgment.

---

*"RAM is finite. Pocket editions make books loadable."*
