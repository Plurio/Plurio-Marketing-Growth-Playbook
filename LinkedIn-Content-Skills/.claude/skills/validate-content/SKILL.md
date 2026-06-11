---
name: validate-content
description: Universal content validator. Orchestrates the check chain — check-facts → check-generic → check-sources → type-specific checks → detect-ai → check-generic (2nd pass). Works for posts, comments, profiles, PR pieces, and event promo.
disable-model-invocation: true
argument-hint: [path-to-content-file] [--type post|comment|profile|pr|event-promo]
allowed-tools: Read, Grep, Glob, Skill(check-facts *), Skill(check-generic *), Skill(check-sources *), Skill(detect-ai *)
---

# Universal Content Validator

Full re-validation of content against ALL canons of the LinkedIn Content Machine via a universal validation chain.

**When to run:**
- Automatically after creating a post via `/create-post`
- After ANY content edits
- Final check before publication
- For comments, PR comments, profile text, promo

## Input

Content file: $ARGUMENTS

Determine `--type` from arguments or from the file contents:
- Has frontmatter with `## Post` → type = `post`
- Has `## Comment` or comment context → type = `comment`
- Has `## Headline` / `## About` → type = `profile`
- Has `## Commentary` → type = `pr`
- Has `## Promo` → type = `event-promo`
- Not detectable → ask the user

---

## PHASE 1: Universal Validation Chain

Invoke in sequence (each runs in isolation):

1. `/check-facts $ARGUMENTS` — facts and logical integrity
2. `/check-generic $ARGUMENTS` — generic language and repetition (FIRST PASS)
3. `/check-sources $ARGUMENTS` — transparent source map

Collect results from all three.

---

## PHASE 2: Type-Specific Checks

Run checks specific to the content type.

### If type = `post`

#### A. Characters and length

Count characters in the `## Post` section (text only, no frontmatter/Brief/Hook Alternatives):

| Range | Verdict | Comment |
|-------|---------|---------|
| 1,200–1,800 | OPTIMAL | Sweet spot: +47% engagement |
| 500–1,200 | OK | For a bold statement / hot take |
| 1,800–2,500 | ACCEPTABLE | Only with a strong hook + story-driven |
| 2,500–3,000 | LONG | Only for exceptional content |
| >3,000 | ERROR | LinkedIn limit exceeded |
| <500 | SHORT | Confirm this was intentional |

#### B. Format and rotation

1. Extract `format:` from frontmatter
2. Read the author's last 5 posts in `Posted/[Author]/`
3. If the format matches 2+ of the last 3 → WARNING with an alternative from `Format-Performance-Data.md`

#### C. Cluster and pillar

1. Extract `cluster:` from frontmatter
2. Compare with DIP Expertise Clusters
3. If outside the DIP clusters → WARNING: Profile-Content Alignment
4. If 5+ posts in a row in the same cluster → WARNING: monotony

#### D. Hook

1. First 1–2 lines of `## Post`
2. If >140 characters → WARNING: it'll be cut by "See more"
3. Compare with hooks from the last 10 posts → if the structure repeats → WARNING

#### E. Anti-Patterns

Load `Knowledge-Base/03-Viral-Trends/Anti-Patterns.md` and check:
- [ ] No engagement bait?
- [ ] No "bro-etry"?
- [ ] No "we/our" in a personal post?
- [ ] No link in the first 300 characters?
- [ ] Not posting within 12h of the previous one?
- [ ] No generic motivational quotes?

#### F. LinkedIn algorithm

Load `Algorithm-Intelligence.md`:
- Structure is readable? Short paragraphs, whitespace
- CTA is specific?
- Profile-Content Alignment?

#### G. Mobile readability

- Paragraphs ≤3 lines?
- Blank lines between blocks?
- No walls of text?

### If type = `comment`

- [ ] Minimum 15 words?
- [ ] First person (I/my)?
- [ ] Not generic ("Great post!", "Love this!")?
- [ ] Not selling/pitching?
- [ ] Doesn't duplicate the original post?
- [ ] No "not X but Y" constructions?
- [ ] No "I've seen..." without specifics?
- [ ] Source grounding passed? (verified fact / grounded inference / question)

### If type = `profile`

- [ ] Headline ≤120 characters?
- [ ] About section: hook in the first 2 lines?
- [ ] No generic descriptions?
- [ ] Specifics: numbers, results, achievements?
- [ ] Tone of voice = DIP?
- [ ] Profile-Content Alignment with clusters?

### If type = `pr`

- [ ] ≤150 words (PR requirement)?
- [ ] Quotable sentence (pullable into a headline)?
- [ ] Not marketing-speak?
- [ ] Tone = the author's DIP?
- [ ] Specifics (numbers, facts, experience)?

### If type = `event-promo`

- [ ] ICP fit: the topic is relevant to the target audience?
- [ ] No generic event descriptions?
- [ ] Concrete value proposition for the attendee?
- [ ] CTA is clear?

---

## PHASE 3: AI Detection & Humanization

Invoke:

4. `/detect-ai $ARGUMENTS` — finds AI patterns and suggests fixes

---

## PHASE 4: Second Pass — Check Generic #2

After detect-ai, the humanizer may have introduced new generic phrasing. Final pass:

5. `/check-generic $ARGUMENTS --second-pass` — verify the humanizer didn't introduce new generic content

---

## PHASE 5: Summary report

```markdown
## Full validation result

### File: [path]
### Content type: [post / comment / profile / pr / event-promo]
### Author: [owner]
### Check date: [today]

---

### Summary

| Check | Status | Detail |
|-------|--------|--------|
| Facts (check-facts) | OK / ATTENTION / CRITICAL | [brief] |
| Generic Pass 1 (check-generic) | CLEAN / NOTES / REWORK | [brief] |
| Sources (check-sources) | OK / ATTENTION | [N] direct, [N] compilations, [N] no source |
| Type-specific checks | OK / NOTES | [brief] |
| AI Detection (detect-ai) | HUMAN / LOW AI / MEDIUM AI / HIGH AI | Score: [N] |
| Generic Pass 2 (check-generic) | CLEAN / NEW ISSUES | [brief] |

---

### Detail: Fact-check
[check-facts result]

### Detail: Generic Pass 1
[check-generic first-pass result]

### Detail: Source Map
[check-sources result]

### Detail: Type-Specific Checks
[per-type results]

### Detail: AI Detection
[detect-ai result]

### Detail: Generic Pass 2
[check-generic second-pass result]

---

### Final recommendations (prioritized)

**Critical (must fix):**
1. [...]

**Important (recommended fixes):**
1. [...]

**Optional (nice to have):**
1. [...]
```

## After edits

The user can re-run `/validate-content [file]`. All checks will rerun against the updated content.
