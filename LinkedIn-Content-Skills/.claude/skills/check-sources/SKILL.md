---
name: check-sources
description: Transparently shows where each key idea in a LinkedIn post comes from. Builds a source map. Lets you exclude specific sources.
disable-model-invocation: true
context: fork
agent: general-purpose
argument-hint: [path-to-post-file]
allowed-tools: Read, Grep, Glob
---

# Source Compilation Tracker Agent

You are an agent that builds a transparent provenance map for every claim in a post. The user should be able to see where each thought came from and have the option to exclude specific sources.

## Input

Post file: $ARGUMENTS

## Algorithm

### 1. Read the post and the sources

- Open the post file
- Extract `source_refs:` from the frontmatter
- Open each source. If the path is relative — resolve from the repo root
- If a file is not found — note it in the report

### 2. Break the post into semantic units

Split the body of the post (`## Post` section) into separate claims / stories / examples. Each unit = one thought, one fact, one example, or one story.

### 3. For EACH unit, find its origin

**Direct quote** — the claim is almost verbatim in a single source:
- List the file, approximate line, verbatim quote from the source
- Note: who said it, in what context

**Compilation** — the claim is assembled from MULTIPLE places:
- Show each fragment separately
- Note: "Fragment A (from source X, context: ...) + Fragment B (from source Y, context: ...) = phrasing in the post"
- Assess: does the context match? Is it about the same thing?

**Author opinion** — the claim isn't found in any source_ref:
- Mark it as the author's position/opinion (this is fine, as long as it isn't presented as fact)

**Common knowledge** — the claim doesn't require a source (e.g., "LinkedIn is the largest professional social network"):
- Mark it as common knowledge

### 4. Reverse check: unused sources

If a source_ref is listed in the frontmatter but nothing from it is actually used in the post — flag it. It may mean:
- The source is redundant (can be removed from source_refs)
- Something was meant to be drawn from it but was forgotten

## Report format

```markdown
## Post source map

### Post: [filename]
### Author: [owner]

### Summary

- Total claims checked: [N]
- Direct quotes: [N]
- Compilations from multiple sources: [N]
- Author opinion (no source): [N]
- Common knowledge: [N]
- Sources not found: [N]

### Full map

| # | Claim in the post | Source(s) | Quote from original | Type |
|---|-------------------|-----------|---------------------|------|
| 1 | "We brought creative testing down to $3.45 per creative" | webinar-transcript.md (~line 145) | "we got it down to three dollars forty five per creative test" | Direct quote |
| 2 | "A team of 3 manages 50+ campaigns" | call-1.md (~line 30) + call-2.md (~line 88) | [quote 1] + [quote 2] | COMPILATION |
| 3 | "Performance marketing is going through a transformation" | — | — | Author opinion |

### Compilations (detail)

For each case where information is assembled from multiple places:

**Compilation #N: "[phrasing in the post]"**
- Fragment 1: `[file]`, ~line N
  - Quote: "[verbatim]"
  - Context: [who said it, about what, in what situation]
- Fragment 2: `[file]`, ~line N
  - Quote: "[verbatim]"
  - Context: [who said it, about what, in what situation]
- **Does the context match?** [Yes / No / Partially — explanation]

### Unused sources

| Source ref | Status |
|------------|--------|
| transcript-X.md | Not used in the post — can be removed from source_refs |

### Recommendations

[If there are problematic compilations or missing sources]
```
