# Token Economy — Meetup Deck

Fully self-contained presentation. No CDN, no build step, no dependencies —
open `index.html` directly in any browser. Keep every `.png` in this folder
next to it (all referenced by relative path).

## Controls
- Arrow keys / space / click the → button to navigate
- `N` toggles speaker notes
- `O` toggles slide overview (grid of all slides, click one to jump)
- `F` toggles fullscreen
- URL hash (`#slide-N`) tracks position — safe to bookmark/reload mid-talk

## Structure (14 slides)
1. Title
2. About me — `me.png` photo + name + bio, 3 real certification badges
   (Claude Certified Architect, AWS Certified Generative AI — Professional,
   AWS Certified Solutions Architect — Professional), two-column layout
3. Vocabulary (6-term grid on top) + 5-stop agenda (arrow flow on bottom)
4. Model selection — tiers, a real-week routing example, anti-habit guidance
5. DeepSWE benchmark — real screenshot from deepswe.datacurve.ai
6. CLI vs. MCP (gh-axi benchmark table + mechanism explanation)
7. Skill-first (escalation ladder + popular skill use cases)
8. Context engineering — real subagents.png + 1m-context-bench.png screenshots,
   real MRCR v2 numbers, "don't run 1M context by default" caution
9. Shell-layer compression — Windows coreutils, ripgrep, RTK with real
   `rtk-gain.png` savings screenshot
10. Headroom — real `headroom.png` screenshot, 4-pass compression explainer,
    JSON-vs-TOON example, package.json case
11. Prompt/read-token caching economics — provider TTL/cost table, worked
    dollar example, one-provider-per-session rule
12. Observability — how to compute $/PR, leading indicators, tooling beyond
    RTK/Headroom (Langfuse, Helicone, OpenTelemetry GenAI conventions)
13. AI-vs-DIY decision triage — concrete criteria + trend-tracking guidance
14. Recap grid + full reference table (tool, purpose, link) — replaces the
    old simple link-pill row

No standalone "section divider" slides — each section's first slide carries a
colored top accent bar and a numbered eyebrow tag (e.g. "01 · Model selection")
instead, to avoid empty low-content slides.

## Design notes
- Layouts are deliberately varied per slide (two-column photo+text, split-30/40/60,
  2×3/2×2 grids, vertical steppers, flow-rows, real screenshot panels) instead of
  repeating one card grid everywhere.
- All benchmark/tooling screenshots are the user's real captures
  (`deepswe-bench.png`, `subagents.png`, `1m-context-bench.png`, `rtk-gain.png`,
  `headroom.png`, `json-vs-toon.png`) — no placeholders remain.
- No Credly links anywhere in the deck — certifications are shown as real badge
  images plus a short text mention of additional certs.
- No together.ai references — DeepSWE is sourced from `deepswe.datacurve.ai`.

## Model-tier guidance
The deck does **not** frame Opus/Fable/Sol as a default. It frames tier choice as
task-driven, and states the personal reference point explicitly: under tight token
budgets, default to Claude Sonnet or GPT-5.6 Luna at high reasoning effort, and
escalate to a frontier model only when the task actually stalls.

## Prompt-caching guidance (slide 11)
Real cache TTLs are short (Anthropic 5 min default/1 hr extended, OpenAI ~5–10 min,
Gemini ~10 min at proxy level) — not 24 hours. The deck states accurate write/read
cost multipliers per provider and a worked example, plus the core recommendation:
stick to one provider/model per work session (switching providers rewrites the
cache from zero), and batch related turns close together so the TTL window doesn't
lapse between them.

## Before you present
1. Re-verify the DeepSWE leaderboard screenshot (slide 5) is still current —
   the benchmark is dated Sept 3, 2026 (v1.1) as of when this deck was built.
2. Double-check current model names/tiers on the "Model selection" slide against
   your provider console on the day of the talk.
3. If any certification has since expired or changed, update slide 2 directly.

## Sources cited in the deck
- DeepSWE: https://deepswe.datacurve.ai/
- gh-axi CLI-vs-MCP benchmark: https://github.com/kunchenguid/gh-axi
- Headroom compression: https://github.com/headroomlabs-ai/headroom
- RTK: https://github.com/rtk-ai/rtk
- Coreutils for Windows: https://github.com/microsoft/coreutils
- ripgrep: https://github.com/BurntSushi/ripgrep
- Langfuse: https://langfuse.com · Helicone: https://helicone.ai

## Verification
Checked with a headless Playwright pass: all 14 `<section>`/`<div>`/`<article>`/
`<header>`/`<footer>` tags balance, all images load, zero JS console errors, zero
failed network/file requests, and keyboard navigation correctly steps through all
14 slides at 1760×990. Every slide was visually reviewed for layout/overflow bugs
(the root cause of earlier "broken layout" issues was a CSS grid `align-content`
default — fixed globally).
