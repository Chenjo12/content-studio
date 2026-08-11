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

**Current focus, effective 2026-08-11: hotel/hospitality content is the priority subject, in Speeed's style.** The creator explicitly directed this — lean into hotel/hospitality subjects (reviews, insider fun facts, hotel history, brand deep-dives, Speeed-style format experiments like "Rise of [Brand]" applied to hotel details) over chasing broad subject variety. The English-learning angle stays in the mix as a compatible secondary layer when it naturally intersects with a hotel/hospitality topic — that combination has already produced some of the strongest ideas (e.g. "Uncomplimentary pants," grading mistranslated hotel signage while teaching the English underneath) — but it's not being pursued as an independent pillar on its own right now.

**Dropped, effective 2026-08-11: the China-for-Western-audience candidate niche.** This was explored as a second content pillar and is now off the table per the creator's explicit direction. Don't propose China-for-Western-audience angles, and don't score ideas or channels on "being genuinely China-based" as an asset going forward.

**Validated format:** "The Rise of the Minibar" (a mock-serious Speeed-style "Rise of [Brand]" parody applied to a hotel minibar) was specifically praised by the creator. Treat mock-serious deep-dives on mundane hotel details, in that exact register, as a strong template worth repeating with new subjects — not a one-off.

## Aspirational model: Speeed (@SpeeedCo)

The creator explicitly points to [Speeed](https://www.youtube.com/@SpeeedCo) (~2.06M subscribers off just 64 videos — hit-driven, not upload-frequency-driven) as the content model they aspire to, specifically for four things:

1. **The magazine-editorial model.** Speeed operates like a GQ-style magazine: the organizing principle isn't a fixed topic niche, it's "would this fit in the same issue of the magazine" — one coherent editorial voice holding together varied subject matter. This maps directly onto this creator's actual background (a real magazine editor at Tatler China). Given the current hotel/hospitality focus (see Content identity above), most content should cohere around that subject, with the magazine-editorial test still useful for judging format experiments and occasional stretches, not as license to wander into unrelated subjects.
2. **Range of subjects — currently narrowed on purpose.** The general principle (a subject is fair game if it fits the same "issue" as the creator's editorial identity, not just if it matches travel) still holds, but given the current hotel/hospitality focus, apply it mostly *within* hotel/hospitality — format experiments and unexpected angles on hotel subjects, not new unrelated pillars. Editorial-coherence stretches outside hotel/hospitality are lower priority right now, not banned.
3. **Video-essay / storytelling format.** Speeed has succeeded with heartfelt, narrative-driven video essays, not just punchy short-form. This is already the creator's own demonstrated strength (see `references/youtube/language-is-reach.md`) and is a format worth leaning into further, not just the shorter hook-driven style.
4. **Genuine engagement, not just insight — but "engaging" is broader than "funny."** Speeed's team came out of Donut Media (irreverent, high-energy car-culture comedy) and is known for subversive, absurdist humor — even its serious/analytical video essays are genuinely entertaining, not dry. **This is a correction, not just an aspiration**: an early batch of content-studio output (2026-08-10) leaned too hard into "editorial credibility = sourced facts + analytical insider framing" and drifted into reading like a news release — technical, hotel-industry-heavy, no life in it. Editorial credibility and being genuinely engaging are not in tension; Speeed proves you can have both. Every idea and every script needs a real hook that isn't just informative — but that hook can be **comedic** (absurd guest requests, a mistranslated sign) or **gripping/dramatic** (a hotel's role in a real historic event, a disaster, a moment of genuine tension) — the throughline is human storytelling energy, not a specific tone. Don't force jokes onto material that calls for gravity instead; forcing comedy onto a tragedy is its own version of the dry-news-release failure, just miscalibrated the other way. Serious subjects (see the hotel-history angle below) need to be handled with real respect and factual rigor — verify carefully, don't sensationalize, and remember real victims/real events deserve accuracy over a punchy hook. This doesn't mean abandoning the creator's own genuine, personal, direct-to-camera voice (see `references/voice-notes.md`) — it means never defaulting to a flat analyst tone, whichever register (funny or gripping) the specific subject actually calls for.
5. **Hotel history as its own deep-dive category.** Beyond reviews and insider-fun-facts, hotels are frequently sites of real historic significance — disasters, political history, notable events, famous guests. Example the creator raised: the 2008 Mumbai terror attacks at the Taj Mahal Palace Hotel. These are gripping, well-suited to the video-essay format, and draw on the same insider/editorial credibility as everything else — but they are **not** comedic material, and factual accuracy matters even more here than usual given the real people and real events involved.

## Working files

- `research/posts/<slug>.md` — per-post research briefs (Story Researcher output)
- `research/strategy/<date>-niche-review.md` — periodic positioning research (Trend Scout output)
- `research/channels/<channel-slug>.md` — per-channel dissections, one file per channel, updated on re-analysis (Channel Analyst output) — feeds Daily Idea Scout
- `research/ideas/<date>-video-ideas.md` — daily batches of concrete video idea candidates (Daily Idea Scout output)
- `scripts/<slug>/{xhs,bilibili,youtube}.md` — platform-adapted drafts with titles (Scriptwriter output)
- `references/` — past best-performing posts per platform, plus `voice-notes.md`, used to match the creator's actual voice rather than defaulting to generic AI-travel-blogger tone

See `docs/superpowers/specs/2026-08-10-content-creation-agents-design.md` for the full design rationale.
