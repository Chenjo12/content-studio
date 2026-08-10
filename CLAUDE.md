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

## Working files

- `research/posts/<slug>.md` — per-post research briefs (Story Researcher output)
- `research/strategy/<date>-niche-review.md` — periodic positioning research (Trend Scout output)
- `scripts/<slug>/{xhs,bilibili,youtube}.md` — platform-adapted drafts with titles (Scriptwriter output)
- `references/` — past best-performing posts per platform, plus `voice-notes.md`, used to match the creator's actual voice rather than defaulting to generic AI-travel-blogger tone

See `docs/superpowers/specs/2026-08-10-content-creation-agents-design.md` for the full design rationale.
