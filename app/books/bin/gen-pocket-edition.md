---
name: gen-pocket-edition
description: Generate pocket edition - compressed book for context loading
---

Generate a **pocket edition** of a book - a compressed representation optimized for context loading.

## Usage

```
/bentos:books:gen-pocket-edition ./books/ontology/
```

## What is a Pocket Edition?

```
pocket_edition = book.essence() + book.structure() + book.navigation()
```

| Component | What It Is |
|-----------|------------|
| **essence** | The irreducible core that makes this book THIS book |
| **structure** | How the book is organized (chapters, flow) |
| **navigation** | Pointers to full content when depth is needed |

### IS

- **Self-contained**: Readable and useful without the original
- **Structural**: Preserves book organization, not just content
- **Navigable**: Points to full content when depth needed
- **Genre-aware**: Compression strategy adapts to book type

### IS NOT

- **Not a summary**: Summaries lose structure
- **Not an abridgement**: Abridgements cut chapters wholesale
- **Not interpretation**: Pocket preserves, doesn't analyze

## Genre-Awareness

The core principle is universal: **preserve essence, compress elaboration**.

What counts as "essence" vs "elaboration" is genre-dependent:

| Book Type | Essence | Elaboration |
|-----------|---------|-------------|
| Technical doc | Concepts, specs, definitions | Examples, walkthroughs |
| Novel | Plot, characters, themes | Scene details, dialogue |
| Philosophy | Arguments, positions | Rhetorical flourishes |
| Poetry | The poems themselves | Commentary, analysis |
| Reference | Definitions, relationships | Extended explanations |
| Tutorial | Steps, outcomes | Detailed instructions |

## Algorithm

1. **Detect**: Validate directory is a book (has README, chapters)
2. **Infer**: Determine genre/purpose from content
3. **Extract**: Per-chapter essence (genre-aware)
4. **Consolidate**: Glossary, cross-references
5. **Generate**: Write `README.pocket.md`

## Output

Single `README.pocket.md` file written to book root.

**Target**: ~20% of original tokens, ~80% signal preserved (heuristic, not rule).

## Quality Criteria

A good pocket edition enables the reader to:

- Understand the book's scope and purpose
- Reference specific concepts by name
- Know the book's structure and flow
- Identify WHEN to consult the full version
- Load multiple pocket editions simultaneously

## Execution

When invoked:

1. Load books.app: `Skill("bentos.books.app")`
2. Validate argument is a book directory
3. Read all chapters to understand content
4. Infer genre from content patterns
5. Apply genre-appropriate compression
6. Generate `README.pocket.md` with:
   - Book metadata (title, source, generated date, chapter count)
   - Book-level essence (3-5 bullets max)
   - Per-chapter essence + key concepts
   - Consolidated glossary
   - Cross-references to other books (if any)
   - Navigation pointers to full content
7. Report compression ratio achieved

---

*"RAM is finite. Pocket editions make books loadable."*
