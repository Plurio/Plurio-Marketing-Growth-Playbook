---
name: AI-Detection-Reference
purpose: "Primary sources on AI content detection on LinkedIn. Used by the detect-ai, check-generic, create-post, and comment-on-post skills as a reference for understanding HOW and BY WHAT CRITERIA LinkedIn ranks and penalizes AI-generated content."
last_updated: 2026-05-21
---

# LinkedIn AI Detection — Reference (what we know, what's confirmed, what isn't)

This file is a short library of primary sources. The skills (detect-ai, check-generic, create-post, comment-on-post) reference it whenever they need to explain WHY a specific rule exists.

---

## 1. 360Brew — LinkedIn's foundation ranking model

This is NOT an AI detector as a standalone system. It is a foundation model that ranks the feed and applies a quality filter (downranking low-effort / AI-generated / off-expertise content).

- **What it is:** 150B-parameter decoder-only LLM (based on LLaMA 3). It replaced the fragmented ranking stack across LinkedIn (feed/jobs/connections).
- **Team:** LinkedIn Foundation AI Technologies.
- **Primary source:** ["Engineering the next generation of LinkedIn's Feed"](https://www.linkedin.com/blog/engineering/feed/engineering-the-next-generation-of-linkedins-feed) — Engineering Blog, **12 March 2026**, Hristo Danchev (Senior Staff TPM).
- **Author's announcement:** [Danchev's LinkedIn post](https://www.linkedin.com/posts/hristodanchev_engineering-the-next-generation-of-linkedin-activity-7437898666096443394-rcTo).
- **Role in detection:** 360Brew consumes detection signals (stylistic embeddings, expertise-author alignment, behavioural signals) and demotes posts classified as AI-slop. The detector architecture itself has not been published.

> **Note:** In voice recordings the term may sound like "BRU360" — it's the same **360Brew** model.

---

## 2. The 94% accuracy claim — what was actually said

- **Said by:** **Laura Lorenzetti, LinkedIn VP of Product**, on the official LinkedIn blog (May 2026).
- **Exact wording (as reported):** "systems correctly identifying generic content 94% of the time" **in early tests**.
- **What was NOT disclosed:** false positive rate, recall, testing methodology, sample size. This is a **precision-only PR figure**, not an engineering-validated benchmark.
- **Policy:** flagged posts are **suppressed in recommendations** (deprioritization), NOT removed. "AI-assisted" content is allowed; the target is "AI slop" (generic, no original insight).
- **Coverage (secondary):**
  - [The Next Web — "LinkedIn cracks down on AI slop with 94% detection accuracy"](https://thenextweb.com/news/linkedin-ai-slop-crackdown-generic-content)
  - [Entrepreneur — "LinkedIn Is Fighting Back Against AI Slop"](https://www.entrepreneur.com/business-news/linkedin-is-fighting-back-against-ai-slop-and-ai-comments)
  - [Fast Company — "LinkedIn declares war on AI slop"](https://www.fastcompany.com/91545007/linkedin-declares-war-on-ai-slop)

> **How to cite in posts/content:** "LinkedIn reports 94% precision in early tests" (citing the speaker and source). NOT "LinkedIn detects AI with 94% accuracy" — that's a simplification that omits the missing FPR.

---

## 3. Confirmed markers (by priority, with links to research)

There is NO canonical "11 markers" list from LinkedIn. The markers below are the intersection of several independent sources, sorted by signal strength.

| # | Marker | Source / research |
|---|--------|-------------------------|
| 1 | **Em-dash (—) overuse** | The most persistent AI signature. [TechRadar "Blade Runners of LinkedIn"](https://www.techradar.com/computing/artificial-intelligence/blade-runners-of-linkedin-are-hunting-for-replicants-one-em-dash-at-a-time), [Plagiarism Today](https://www.plagiarismtoday.com/2025/06/26/em-dashes-hyphens-and-spotting-ai-writing/) |
| 2 | **"It's not X, it's Y" contrast framing** | Explicitly named by LinkedIn as a demotion target |
| 3 | **Uniform sentence length / rhythm** | Adrian Vega's 500-post study |
| 4 | **Rule-of-three abuse** (everything in lists of 3) | Cross-source pattern |
| 5 | **Formal transitions** (moreover / furthermore / however) | Cross-source pattern |
| 6 | **One sentence per line + blank line between** | 91% of AI posts — Adrian Vega's study |
| 7 | **Generic opener templates** ("Here's the thing", "Let me share") | 82% of AI posts use 3 opener templates — Adrian Vega |
| 8 | **Absence of specific numbers / names / dates** | Cross-source pattern |
| 9 | **Absence of personal POV / interchangeable authorship** | Cross-source pattern |
| 10 | **Sparse or symmetric use of emoji** | Cross-source pattern |
| 11 | **Absence of humor / irony / nuance** | Cross-source pattern |

---

## 4. Behavioural detection signals (what LinkedIn actually uses)

LinkedIn explicitly uses **behavioural + stylistic signals** (NOT watermarks — they confirmed it's "fuzzier than image detection"). Documented signals:

- **Posting cadence anomalies** — a sharp spike (2x/week → 10x/hour) is flagged as spam/bot
- **InMail volume spikes** (200+/day = bot signal)
- **First 90 minutes engagement velocity** — primary reach determinant (van der Blom)
- **Stylistic embeddings via 360Brew** — semantic similarity to known AI patterns
- **Author-expertise alignment** — 360Brew checks whether a post's topic matches stated expertise; mismatch = downrank
- **Engagement bait detection** — AI comment spam from automation tools is targeted separately

**NOT confirmed (speculation):** specific thresholds, exact feature weights, per-user "AI score". The detector architecture has not been published.

---

## 5. Top expert sources

### Adrian Vega — empirical study (500 AI posts)

- [dev.to — "I Analyzed 500 AI-Generated LinkedIn Posts"](https://dev.to/adrianvegaresearch/i-analyzed-500-ai-generated-linkedin-posts-heres-what-they-all-have-in-common-2h36)
- **Key numbers:**
  - 82% of AI posts use 3 opener templates
  - 91% use the "one sentence per line + blank line between" format
  - "AI-polished" posts get **5x LESS engagement** than low-polish posts (counter-intuitive insight: cleaning up kills reach)
- **Application:** when editing drafts, don't "smooth them over" — leave the human roughness.

### Richard van der Blom — Algorithm Insights Report (annual)

- [Chapter 1 — Algorithm Insights Report 2025](https://www.linkedin.com/posts/richardvanderblom_chapter-1-algorithm-insights-report-2025-activity-7322514599126130688-Q895)
- Data-driven LinkedIn behavioural research (sample of 1.3M posts in the 2026 edition).
- **Application:** for understanding the algorithm — golden window, posting time, format performance.

### Originality.ai study

- [LinkedIn AI Engagement Study](https://originality.ai/blog/linkedin-ai-study-engagement)
- 50%+ of long LinkedIn posts have been AI-generated since the launch of ChatGPT.
- AI-likely posts get **45% less engagement**.

---

## 6. What from this is reflected in our skills (mapping)

| Marker from reference | Skill / level |
|---------------------|-----------------|
| Em-dash overuse | `detect-ai` Level 3A + memory `feedback_no_em_dashes` |
| "Not X, but Y" contrast | `detect-ai` Level 4F + memory `feedback_avb_contrast_must_be_specific` |
| Uniform sentence length | `detect-ai` Level 2A + 6A (burstiness) |
| Rule of three | `detect-ai` Level 3E |
| Formal transitions | `detect-ai` Level 1 (transition fillers) |
| One sentence per line | `detect-ai` Level 6B (paragraph length) |
| Generic openers | `detect-ai` Level 4G + `check-generic` |
| Lack of specifics | `detect-ai` Level 5A + 5C |
| Generic motivational endings | `check-generic` ban list |
| Author voice missing | `detect-ai` Level 7 (Voice Authenticity) + Voice Vocabulary file |
| Comments written like posts | `comment-on-post` rule "comments NOT as posts" |
| Posting cadence anomalies | NOT in text skills — this is operational/posting strategy |

---

## 7. What to update next time

- When the [Algorithm Insights Report 2026 by van der Blom] is released — update the numbers
- When LinkedIn publishes an engineering paper on the detector — add the architecture (if they publish one)
- Voice Vocabulary files — update every time a new author is added (see `_Voice-Vocabulary/`)
