# Article: Why Your CRM Is Missing 30-40% of Lead Sources (And the Open-Source Fix)

> **Author:** Seva Ustinov (heavy credit to Andrey Konoplya throughout)
> **Format:** LinkedIn Article (GEO-optimized for AI search citations)
> **Target length:** 1,500-1,800 words
> **Publish:** 2026-04-29 (Wednesday – default, adjustable within next week), morning LA / afternoon CET
> **Related Seva post:** [2026-04-22-data-foundation-before-agent.md](../Posted/Seva/2026-04-22-data-foundation-before-agent.md) – published a week earlier as a standalone; drove initial traffic to Andrey's 3 posts. This article is the extended, deeper follow-up published a week later to give the initial post room to breathe and provide a second wave of intake traffic.
> **Sources (all verified):**
>
> - Andrey Konoplya LinkedIn post 1 (problem breakdown, 2026-04-21): https://www.linkedin.com/feed/update/urn:li:activity:7449736518660874240/
> - Andrey Konoplya LinkedIn post 2 (9-point checklist carousel, 2026-04-22): https://www.linkedin.com/feed/update/urn:li:activity:7450473386008338433/
> - Andrey Konoplya LinkedIn post 3 (Intake announcement, 2026-04-22): https://www.linkedin.com/feed/update/urn:li:activity:7451890348336877568/
> - Intake landing page: https://intake.plurio.ai/#getting-started
> - Seva DIP for voice
>   **GEO keywords:** marketing attribution gap, UTM tracking library, open source click ID tracking, multi-touch attribution library, lead source tracking, consent mode v2 attribution, SPA UTM tracking, Safari ITP attribution, AI agent data foundation, CRM attribution integration

---

## ARTICLE TEXT

# Why Your CRM Is Missing 30-40% of Lead Sources (And the Open-Source Fix)

If you opened your CRM right now and pulled leads from the last 90 days, you'd probably find that 30-40% of them have no source data. Not "direct traffic." Not "Google / Organic." Blank. Missing. Never collected.

This isn't a reporting bug. It's a data collection problem. And it's the single biggest reason marketing attribution doesn't work – whether you're running spreadsheets, a dashboard tool, or an AI agent on top of your stack.

This article explains why the gap exists, what it actually costs you, and how to fix it in three lines of code using [Intake](https://intake.plurio.ai/) – an open-source library my Head of Product, Andrey Konoplya, released this week under the MIT license.

## The part nobody wants to talk about

Every time our team at Plurio starts a new analytics implementation, we begin the same way: open the client's CRM, look at what's being stored with each lead, and count the records with empty UTMs, no click IDs, and no analytics identifiers.

The answer is almost always the same: 30-40%.

Those leads didn't come from "direct traffic." They came from paid search, paid social, affiliates, influencers, podcast links, email – but somewhere between the ad click and the CRM record, the source data was lost.

You can build the smartest attribution model in the world on top of that data. It will still be wrong by a third.

## Why the data gets lost: nine real problems

Andrey spent months breaking this down across 100+ of our own analytics projects. The result is a list of nine things that every production website needs to solve for attribution to actually work. I'll summarize each briefly – his three LinkedIn posts go deeper into any single one.

### 1. Redirects silently strip URL parameters

A 301 between your ad's click URL and the landing page drops every UTM and click ID. Short-link platforms, auth flows, login gates, domain consolidation redirects – each one is a silent drop. You won't see it until you walk the redirect chain in DevTools.

### 2. Single-page apps don't reload

React, Vue, Angular. The URL changes via `history.pushState` on internal navigation, but the page doesn't reload. Your analytics script reads the URL *after* the app router has already rewritten it – the UTM parameters are gone from the address bar by the time anything is captured.

### 3. Safari's 7-day cookie rule

Safari's Intelligent Tracking Prevention expires JavaScript-set cookies after 7 days. A user clicks your ad on Monday, comes back the following Tuesday – Safari doesn't remember them. Source: "direct." That's roughly 30% of global web traffic treated as new every week.

### 4. In-app browsers sandbox cookies

A user taps your ad inside Instagram – the landing page opens in Instagram's in-app browser with its own cookie jar. They close the app, open Chrome, come back later. Different cookie sandbox. Different session. Conversion: "direct."

### 5. Consent banners shut tracking off

In the EU, roughly 35% of users decline cookies. Standard analytics writes nothing for those visitors – no session, no source, no downstream attribution. That's not a bug; it's the regulation working as intended. But it still means you need a plan for pre-consent data that doesn't violate the regulation.

### 6. Cross-domain transitions

`site.com` → `checkout.site.com` → `pay.vendor.com`. Every domain hop is a new session unless you explicitly pass identifiers across. Most checkouts don't. The lead that finally converts looks like they came from your checkout domain itself.

### 7. Eleven click ID types, each with its own rules

`gclid`, `fbclid`, `ttclid`, `msclkid`, `li_fat_id`, `wbraid`, `gbraid`, `twclid` – every major ad platform uses its own. Without capturing and routing them server-side, you can't send conversions back through the platform APIs to close the optimization loop (Google Ads Enhanced Conversions, Meta CAPI, TikTok Events API, and the rest).

### 8. Analytics IDs scattered across tools

GA4 Client ID, Amplitude ID, Mixpanel `distinct_id`, custom identifiers. They each live in their own cookies or localStorage entries. Without stitching them together at capture time, you can't reconcile the same visitor across tools.

### 9. Legacy scripts nobody owns

Every long-running website has a tracking script written by a developer who left three years ago. Nobody knows what logic it has, what edge cases it covers, or what it breaks when the site's framework updates. It keeps running in production, and the team just hopes it still works.

Each of these is its own engineering fight. Solving them all cleanly is two to four weeks of dedicated dev work per project – plus maintenance forever after, because browsers, consent regulations, and ad platforms keep changing.

Which is why most teams just… don't. They launch the AI agent, the dashboards, and the rules engine on top of a foundation that's 30-40% missing. Then they wonder why the attribution numbers don't match reality.

## The cost of "we'll fix it later"

Here's the part that most teams miss: data you don't collect today is lost forever.

You can always re-run a report next quarter. You cannot go back and ask where last quarter's leads came from. If the UTM didn't hit your CRM on the day the lead filled out the form, that information doesn't exist anywhere else in your stack.

This means every day you run with broken tracking compounds the gap in your historical data. Three months of missing source data on 30-40% of your leads is three months you can't analyze, can't cohort, can't model.

For performance teams running six or seven figures a month in ad spend, that's not a nice-to-have problem. That's the single biggest blind spot in the decision-making stack.

## The fix: Intake, open source, three lines of code

Andrey looked at the same nine problems over and over, project after project, and realized 80% of the implementation work was the same repetitive plumbing. So he wrote it once, properly, and we're releasing it under MIT.

[Intake](https://intake.plurio.ai/) is a lightweight JavaScript library that captures every visitor touchpoint from initial click to conversion, then hands the data to whatever analytics and attribution stack you already use. It's ~14 KB gzipped, has zero external dependencies, and installs in three lines:

```javascript
import intk from '@plurio/intake';

intk.init({
  domain: 'yoursite.com',
  callback: function(data) {
    console.log('Source:', data.current.src);
  }
});
```

That's it. Once initialized, Intake handles all nine problems above automatically:

- **UTM parsing and persistence** – first-touch and current-source stored separately; survives SPA navigation via History API hooks
- **11 click IDs** captured and preserved for server-side forwarding (Google Ads, Meta CAPI, TikTok Events, LinkedIn, Microsoft, Twitter)
- **Consent Mode v2** native, with 10+ CMPs supported out of the box (OneTrust, Cookiebot, Axeptio, Didomi, Sirdata, Termly, TrustArc, Iubenda, Klaro, Quantcast, Consentmo)
- **Analytics ID stitching** – GA4 Client ID, Amplitude, Mixpanel `distinct_id`, and custom IDs all collected on the same record
- **PII hashing** – SHA-256 for emails and phones at capture time; raw PII never leaves the browser
- **Link decoration** – auto-decorates external links with UTM and click IDs for clean cross-domain flow
- **SPA tracking** – History API hooks, no manual wiring per route
- **CRM integration** – hidden form fields auto-populate, or callback to your own API
- **Five attribution models built in** – first touch, last touch, linear, U-shaped (40/20/40), time decay (7-day half-life)
- **Server-side ready** – click IDs, consent state, and touchpoint chains routed server-side for CAPI / Ads API calls

### Install paths

Use whichever fits your setup:

- **CDN** (jsDelivr): one script tag, no build tools
- **npm / ESM**: `npm install @plurio/intake`
- **Self-hosted**: download and host the file yourself
- **Google Tag Manager**: pre-made JSON container import, ES5-compatible build included

### A more complete config

```javascript
intk.init({
  domain: 'yoursite.com',
  data_layer: true,
  spa_tracking: true,
  pii_collection: true,
  url_passthrough: true
});
```

Touchpoint capacity is up to 50 per visitor, which is more than enough for almost any realistic funnel.

## Why open source

A fair question: why give this away instead of keeping it behind Plurio?

Because this is the foundation everyone needs, regardless of what they're building on top. An agency running dashboards for clients needs it. An in-house analytics team running Looker or Metabase needs it. A team building their own AI agents for marketing needs it. We need it for our own clients.

Closing up a library like this behind a paywall just ensures that 30-40% of everyone's leads continue to show up as "direct traffic." That's not good for the industry, and honestly it's not good for us either – we'd rather compete on the AI agent on top of clean data than on owning the plumbing underneath.

MIT license. Take it, ship it, modify it. If you find an edge case we missed, send a PR.

## What this unlocks for AI agents

One more note, because this article is also for the founders and operators evaluating AI marketing agents.

Every AI marketing agent – ours included – sits on top of analytics data. If that data is 30-40% broken before the agent ever turns on, the agent's decisions are going to be 30-40% broken too. No amount of clever prompting or fine-tuning fixes bad input.

If you're thinking about bringing an AI agent into your performance stack, this is step zero. Ship the data foundation first. Then the agent has something real to work with.

## How to get started

1. Go to [intake.plurio.ai](https://intake.plurio.ai/#getting-started) for the live demo and full documentation.
2. Read Andrey's three LinkedIn posts – the problem, the 9-point checklist, and the release – all linked in the first comment below.
3. If you want Andrey's step-by-step implementation guide (from install to data showing up in your CRM), comment INTAKE on his [announcement post](https://www.linkedin.com/feed/update/urn:li:activity:7451890348336877568/). He's sharing it with anyone who asks.

Before you buy the agent, ship the foundation.

---

## Metadata

- **Word count target:** 1,500-1,800 (final draft ~1,650-1,750 after trims)
- **Tone:** Seva voice – direct, framework-thinker, observation-based authority, first person ("our team", "we", "I"), no "20 years in performance marketing" (per feedback_seva_overused_authority_phrases memory), no "ITA Agency"
- **Andrey credit:** Named in lead paragraph + "our team" throughout + 3 post links at close
- **GEO optimization:** Opening paragraph is a direct answer (pattern matches queries like "why is my marketing attribution broken", "why is source data missing in CRM"); H2s are also query-like phrasings
- **CTA hierarchy:**
  1. intake.plurio.ai (product surface)
  2. Andrey's 3 posts (traffic to Andrey's audience)
  3. Comment INTAKE on Andrey's announcement (lead-gen into DMs)
- **Links verified:** 3 LinkedIn post URLs + intake.plurio.ai confirmed

## Companion post

The 2026-04-23 Seva teaser post ([2026-04-23-data-foundation-before-agent.md](../Posted/Seva/2026-04-23-data-foundation-before-agent.md)) should be updated to reference this article – add a line like "Full article with the 9 technical problems broken down + install guide: [link]" or include the article as the thing he's sending people to (instead of Andrey's posts directly).

## Open questions for user

1. Do we want Seva's 2026-04-23 post to link to this article (pulling people here first) or directly to Andrey's posts? If article, I update the teaser post; if Andrey's posts, keep teaser as-is.
2. Confirm article publishes on Seva's profile (not Andrey's). Consistent with existing Articles plan.
3. Any brand-voice adjustments before I treat this as publish-ready (e.g., "our team" vs "my team", "we" vs "I" balance)?
