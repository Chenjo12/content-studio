# Content Studio

This project holds subagents and working files for a solo content creator's research → scripting pipeline. Every agent in `.claude/agents/` should read this file as shared context.

## Who this is for

A luxury travel/lifestyle content creator distinguished by real editorial and industry credentials, not pure influencer framing:
- Freelance travel editor for Tatler China
- Graduate of Swiss hotel management education
- Collaborations with top-tier hospitality brands: Bvlgari (London, Paris), Four Seasons (Maldives, Bali), Capella Hotels, W New York, Wynn Palace Macau

This professional/editorial layer is the account's core differentiator. Content should draw on real industry knowledge, not generic travel-blogger observations — and should never fabricate specifics about a real property or brand.

## Platform footprint

- **Xiaohongshu (XHS)** — core platform, ~64K followers, 225K+ likes/saves, content primarily in English, run as a culture-blogger (文化博主) account.
- **Bilibili** — shares the XHS audience; better suited to longer-form content and potential paid knowledge products.
- **YouTube** (@johnnycchen) — smaller/less active (~1,350 subscribers), watch-hours-constrained for YPP. English-learning content has historically outperformed pure travel content here.

## Content identity

A deliberate hybrid pillar: luxury travel/hotel content combined with English-learning content, aimed at a Chinese audience wanting both aspirational travel content and practical language value.

A second candidate niche under active exploration: content about life/culture in China, framed for a Western/English-speaking audience — leveraging that the creator is genuinely based in China at times, plus real hospitality-industry access most "China content" creators lack. See `research/strategy/` for the latest niche analysis on this.

## Aspirational model: Speeed (@SpeeedCo)

The creator explicitly points to [Speeed](https://www.youtube.com/@SpeeedCo) (~2.06M subscribers off just 64 videos — hit-driven, not upload-frequency-driven) as the content model they aspire to, specifically for four things:

1. **The magazine-editorial model.** Speeed operates like a GQ-style magazine: the organizing principle isn't a fixed topic niche, it's "would this fit in the same issue of the magazine" — one coherent editorial voice holding together varied subject matter. This maps directly onto this creator's actual background (a real magazine editor at Tatler China) and their hybrid-pillar problem: travel/hospitality, English-learning, and the candidate China-for-Western-audience niche don't need to be treated as separate lanes if they cohere under one editorial identity the way Speeed's cars/lifestyle/tech content does.
2. **Range of subjects.** Ideas aren't confined to a narrow "luxury travel" box. A subject is fair game if it would credibly fit the same "issue" as this creator's established editorial identity (hospitality-industry insider perspective, cross-cultural/language lens) — the test is coherence with that identity, not topic-matching to travel specifically.
3. **Video-essay / storytelling format.** Speeed has succeeded with heartfelt, narrative-driven video essays, not just punchy short-form. This is already the creator's own demonstrated strength (see `references/youtube/language-is-reach.md`) and is a format worth leaning into further, not just the shorter hook-driven style.
4. **Humor and fun, not just insight.** Speeed's team came out of Donut Media (irreverent, high-energy car-culture comedy) and is known for subversive, absurdist humor — even its serious/analytical video essays are genuinely entertaining, not dry. **This is a correction, not just an aspiration**: an early batch of content-studio output (2026-08-10) leaned too hard into "editorial credibility = sourced facts + analytical insider framing" and drifted into reading like a news release — technical, hotel-industry-heavy, no fun in it. Editorial credibility and being genuinely entertaining are not in tension; Speeed proves you can have both. Every idea and every script needs an actual fun/playful angle, not just an informative one — if an idea only works as analysis, it's not ready yet. This doesn't mean abandoning the creator's own genuine, personal, direct-to-camera voice (see `references/voice-notes.md`) for Speeed's specific comedic style — it means adding real wit and playfulness on top of that authenticity, instead of defaulting to a serious analyst tone.

## Working files

- `research/posts/<slug>.md` — per-post research briefs (Story Researcher output)
- `research/strategy/<date>-niche-review.md` — periodic positioning research (Trend Scout output)
- `research/ideas/<date>-video-ideas.md` — daily batches of concrete video idea candidates (Daily Idea Scout output)
- `scripts/<slug>/{xhs,bilibili,youtube}.md` — platform-adapted drafts with titles (Scriptwriter output)
- `references/` — past best-performing posts per platform, plus `voice-notes.md`, used to match the creator's actual voice rather than defaulting to generic AI-travel-blogger tone

See `docs/superpowers/specs/2026-08-10-content-creation-agents-design.md` for the full design rationale.
