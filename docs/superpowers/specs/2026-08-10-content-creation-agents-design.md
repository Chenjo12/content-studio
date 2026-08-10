# Content Creation Agents — Design

**Date:** 2026-08-10
**Status:** Approved for implementation planning

## Context

The user is a solo luxury travel/lifestyle content creator with real editorial credentials (freelance travel editor for Tatler China, Swiss hotel management graduate, collaborations with Bvlgari, Four Seasons, Capella, W, Wynn Palace, among others) — a professional/editorial layer that differentiates the account from typical travel-influencer content.

Platform footprint:
- **Xiaohongshu (XHS)** — core platform, ~64K followers, 225K+ likes/saves, content primarily in English, run as a culture-blogger account.
- **Bilibili** — shares the XHS audience, better suited to longer-form and paid knowledge-product content.
- **YouTube** (@johnnycchen) — smaller/less active (~1,350 subscribers), watch-hours-constrained for YPP. English-learning content has historically outperformed pure travel content here.

Content identity is a deliberate hybrid pillar: luxury travel/hotel content combined with English-learning content, aimed at a Chinese audience wanting both aspirational travel content and practical language value. The user is also exploring a second candidate niche — content about life/culture in China framed for a Western/English-speaking audience, leveraging the fact that they are genuinely based in China at times, plus their hospitality-industry access.

The user's pipeline spans ideation, research, scripting, editing/post-production, and publishing/distribution across these three platforms. This spec covers the highest-leverage slice first: **ideation & scripting, and research.** Editing/post-production (including thumbnail design) and the rest of publishing/distribution are explicitly deferred to a later sub-project.

## Goal

Give the user a small set of focused Claude Code subagents that expedite the research → scripting portion of their content pipeline, without collapsing distinct jobs (fast per-post lookups vs. periodic strategic analysis vs. writing) into one muddy agent.

## Location

A new, dedicated project: `~/Documents/content-studio` (separate git repo). Content creation isn't tied to any existing codebase, so the agents are defined globally to that project rather than living inside an unrelated repo.

## Project structure

```
content-studio/
  .claude/
    agents/
      story-researcher.md      # per-post research
      trend-scout.md           # periodic strategy/niche research
      scriptwriter.md          # cross-platform script/caption/title drafting
  CLAUDE.md                    # positioning, platforms, hybrid pillar — context every agent needs
  research/
    posts/<slug>.md            # one research brief per post (Story Researcher output)
    strategy/<YYYY-MM-DD>-niche-review.md   # periodic Trend Scout output
  scripts/
    <slug>/
      xhs.md
      bilibili.md
      youtube.md
  references/
    youtube/                   # 2-3 best-performing past YouTube scripts/transcripts
    xhs/                       # 2-3 best-performing past XHS posts
    bilibili/                  # optional, can start empty
    voice-notes.md             # explicit voice descriptors (see below)
```

`<slug>` is a short per-post identifier (e.g. `w-macau-checkin`) so a research brief and its resulting scripts pair up predictably.

## Components

### 1. Story Researcher

**Purpose:** Given a specific hotel/destination/brand/topic for an upcoming post, produce a research brief grounding the content in real editorial detail — not generic travel-blogger copy.

**Invoked when:** Starting a specific post with a known subject.

**Input:** Topic/subject, target platform(s) if known, any raw notes already in hand.

**Output:** `research/posts/<slug>.md` containing:
- Brand/destination facts (history, design story, notable architects/chefs — editorially interesting detail, not an amenities list)
- 2-4 competitive reference posts/videos on the same or similar property: angle taken, and performance if visible
- SEO/hashtag suggestions for XHS discoverability
- Source links for every factual claim

**Tools:** WebSearch, WebFetch, firecrawl (search/scrape) for deeper reads, Write.

**Depends on:** Nothing. Leaf node; Scriptwriter optionally consumes its output.

**Error handling:** If a fact can't be verified or sources conflict, the brief flags the uncertainty explicitly rather than smoothing it over. Editorial credibility is the account's core differentiator, so a confidently wrong fact is worse than a visible gap.

### 2. Trend & Niche Scout

**Purpose:** Periodically analyze the competitive landscape across XHS, Bilibili, and YouTube to spot content gaps and recommend positioning. Answers "what should I be making more of," not "research this hotel."

**Invoked when:** Periodically — roughly monthly, or whenever the user wants to sanity-check direction — rather than per post.

**Input:** Which platform(s) to focus on; optionally a hypothesis to pressure-test (e.g. "is China-life content for Western viewers worth pursuing?").

**Output:** `research/strategy/<date>-niche-review.md` containing:
- What's currently gaining views/engagement in adjacent niches on each platform, with examples
- 3-5 concrete content angle recommendations, each scored on fit with the user's actual assets (editorial credentials, hospitality access, being China-based, English-learning angle) rather than generic trend-chasing
- For YouTube specifically: gap analysis against channels succeeding at "China for Western audiences" or "English-learning + lifestyle" — the two nearest proven lanes given current performance data

**Tools:** WebSearch, WebFetch, firecrawl (search/scrape), Write.

**Depends on:** Nothing. Leaf node, independent of Story Researcher.

**Error handling:** XHS in particular is hard to search/scrape from outside China-facing tools. Where real data isn't accessible, the review says so explicitly rather than presenting a guess as an observed trend.

### 3. Cross-Platform Scriptwriter

**Purpose:** Turn a topic — with or without a research brief — into platform-adapted drafts for XHS, Bilibili, and YouTube in one pass, since repurposing across 2-3 platforms is the normal case, not an edge case. Also produces a platform-specific **title** per output (titles are text and closely tied to hook/retention work this agent already owns), covering "packaging" text; thumbnail design is out of scope (see Deferred).

**Invoked when:** A subject is ready to draft. Two entry points:
- If `research/posts/<slug>.md` exists, it's pulled in automatically for facts/SEO angles.
- If not, the agent drafts directly from raw notes — research isn't a hard requirement, since some posts are low-stakes or already well-known to the user.

**Input:** Slug/topic, raw notes (if no research brief exists), which platform(s) to draft for (default: all three).

**Output:** `scripts/<slug>/{xhs,bilibili,youtube}.md`, each including a title plus body shaped for its platform:
- **XHS:** hook-driven caption, English-primary per existing style, hashtag block
- **Bilibili:** longer-form narrative/outline; initially derived/adapted from the YouTube or XHS draft rather than receiving bespoke hook/retention treatment
- **YouTube:** script with explicit hook/retention structure (first-class priority alongside XHS), room for an English-learning segment given it's the best-converting angle on this platform

**Voice matching:** Reads `references/<platform>/` examples and `references/voice-notes.md` before drafting. Voice notes capture explicit descriptors distilled from the user's best-performing YouTube video: direct-to-camera, "straightforward and genuine" (self-described inspiration: Casey Neistat, Peter McKinnon), short punchy lines mixed with longer reflective ones, real personal anecdotes as the backbone, rhetorical questions to the viewer, genuine (non-performative) code-switching between languages mid-script when it serves the point, and grounding abstract ideas in concrete personal stories.

**Tools:** Read (research brief, reference files), Write (scripts). Deliberately no web-search tools — this agent writes, it doesn't research, so it can't wander into research when it should be drafting.

**Depends on:** Optionally reads Story Researcher's output. Does not depend on Trend Scout — the user reads a strategy review themselves and passes the resulting angle in as input.

**Error handling:** If given neither a research brief nor raw notes for a real property/brand, the agent asks rather than inventing specifics — fabricated hotel details would undermine the exact credibility the account is built on.

## Data flow / composition

The three agents are independent and chained manually by the user — no orchestration layer:

1. **Periodically (~monthly):** run Trend & Niche Scout → review output → decide direction (e.g. "try a China-for-Western-audience angle this month").
2. **Per post:** run Story Researcher with a subject → produces `research/posts/<slug>.md`.
3. **Per post:** run Scriptwriter with the same slug → picks up the research brief and reference voice files → produces XHS/YouTube (and, once first-class, Bilibili) drafts with titles.

Keeping the user as the manual link between steps preserves editorial judgment in the loop rather than letting the pipeline run unattended.

## Validation approach

These are prompt-defined agents, not code — there's no automated test suite. Validation is a real dry run per agent against an actual topic once each is built, checking output usability (tone match, factual grounding, platform fit), then tightening the agent's instructions based on what's off.

## Explicitly deferred (next sub-project)

- **Thumbnail Designer agent** — visual packaging (thumbnails), using the image-generation tooling available in this environment. Deserves its own design pass since it's a genuinely different kind of work (visual, not text) from everything in this spec.
- Editing/post-production more broadly (captions, b-roll, quick cuts).
- The rest of publishing/distribution (descriptions, tags beyond SEO hashtags already covered by Story Researcher, community replies).
