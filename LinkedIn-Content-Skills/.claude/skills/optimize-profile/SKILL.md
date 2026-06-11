---
name: optimize-profile
description: Pipeline for optimizing an author's LinkedIn profile. Headline → About → Experience → Skills → Photo/Banner → Verifications. Every element is checked against 360Brew's Profile-Content Alignment. The result is run through /validate-content --type profile.
disable-model-invocation: true
argument-hint: [Author]
allowed-tools: Read, Grep, Glob
---

# Optimize LinkedIn Profile

Pipeline for LinkedIn profile optimization with validation through the universal validation chain.

## Input

- `$0` — author name (Seva, Kirill, Plurio)

## Required files

1. **Author DIP:**
   `Knowledge-Base/01-Identity-Profiles/[Author]-DIP.md`
   → Expertise Clusters, Tone of Voice, Identity

2. **Profile-Optimization-Guide:**
   `Knowledge-Base/08-Profile-Optimization/Profile-Optimization-Guide.md`
   → Formulas, benchmarks, recommendations

3. **Algorithm-Intelligence:**
   `Knowledge-Base/02-LinkedIn-Algorithm/Algorithm-Intelligence.md`
   → 360Brew Profile-Content Alignment

4. **Posted (recent posts):**
   `Posted/[Author]/`
   → To assess Profile-Content Alignment

## Why Profile-Content Alignment is critical

360Brew **cross-checks** post content against the profile (Headline, About, Experience).
**Semantic mismatch** → **distribution suppression**.

Statistics:
- Profiles with a photo → 3× connection requests, 2× profile views
- Verified profiles → 60% more profile views
- 5+ skills → 2.9× profile views, 4.7× messages

## Pipeline

### Step 1: Audit the current profile

Ask the user for current profile data (or a screenshot):
- Headline
- About / Summary
- Experience entries
- Skills (listed)
- Photo / Banner
- Verifications

### Step 2: Headline Optimization

**Formula:** `[Role/Identity] | [Core Expertise 1] + [Core Expertise 2] | [Unique Differentiator]`

**Rules:**
- Max 220 chars, first 60 are visible in the feed
- Keywords from post topics are REQUIRED (360Brew alignment)
- No buzzwords: "Thought Leader", "Visionary", "Guru", "Passionate"

**Process:**
1. Extract from the DIP: core identity, expertise clusters
2. Analyze the last 10 posts → extract keywords
3. Propose 3 headline variants
4. Check: do the first 60 chars contain the most important thing?

### Step 3: About Section

**Formula (5 paragraphs):**

```
P1: Hook — statistic/provocation (2 lines)
P2: Who I am — identity statement + credential
P3: What I'm doing — current project + mission
P4: What's in my past — credibility markers
P5: CTA — how to reach me / what I offer
```

**Rules:**
- First 2 lines = hook (visible without "See more")
- First person (I/my)
- Specifics: numbers, results, named entities
- Tone = author's DIP
- Keywords from Expertise Clusters

### Step 4: Experience

- Each role: 2–3 bullet points with results
- Concrete metrics: revenue, team size, clients
- Keywords for search

### Step 5: Skills

- Minimum 5 skills (threshold for the 2.9× boost)
- Skills = keywords from Expertise Clusters
- Order: most important on top

### Step 6: Photo & Banner

**Photo:**
- Professional, face fills 60–70% of the frame
- Smile, direct gaze

**Banner:**
- Contains a value proposition or brand statement
- Not overloaded with text

### Step 7: Verifications

- Email verification → +60% profile views
- Phone verification
- Company verification (if available)

### Step 8: Validation

Suggest the user run `/validate-content --type profile` on the resulting text.

## Output

```markdown
## Profile Optimization Report — [Author]

### Date: [today]

---

### Headline

**Current:** [current headline]

**Variant 1:** [headline]
**Variant 2:** [headline]
**Variant 3:** [headline]

**Recommendation:** Variant [N] — [why]
**Profile-Content Alignment:** [keywords from posts that are covered]

---

### About Section

[Full About text — 5 paragraphs]

**Characters:** [N]
**Keywords covered:** [list]

---

### Experience (update recommendations)

[For each role: recommended bullet points]

---

### Skills (recommended order)

1. [skill] — [why it matters]
2. [skill]
...

---

### Checklist

- [ ] Headline updated
- [ ] About updated
- [ ] Experience updated
- [ ] Skills added (5+)
- [ ] Photo checked
- [ ] Banner updated
- [ ] Verifications passed
- [ ] Profile-Content Alignment verified
```

## Quarterly Audit

Profiles should be revisited quarterly or whenever content strategy shifts. If the DIP's Expertise Clusters changed → headline and About need to be updated.
