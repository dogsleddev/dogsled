# dogsled.dev landing — Kickoff for Antigravity / Claude Code

## What this project is

A single-page landing for `dogsled.dev` — a builder's log for modern finance. Wordmark, tagline, a reverse-chronological list of modules (newest on top), and links to the live tools (`freightclose.dogsled.dev`, `staff.dogsled.dev`, `artool.dogsled.dev`).

Status: bare-bones, intentionally. Ships today. Evolves from here.

## Read this first

The most important file in this project is `dogsled-brand/SKILL.md`. It's a complete brand system with tokens, type, color, motion, mark, voice, and the status pill vocabulary. Anything you generate for this project should pull from that skill.

Other files to know:

- `index.html` — the landing page itself. Single file, no build step.
- `dogsled-brand/references/tokens.css` — canonical CSS variables for both themes.
- `dogsled-brand/references/components.md` — pill, topbar, theme toggle, atmosphere patterns.
- `dogsled-brand/references/voice.md` — voice and copywriting rules.
- `dogsled-brand/references/anti-ai-tells.md` — how to NOT sound like generic AI output.

## How to work with me on this project

**Voice.** I'm Chris. I write casual ("brudha", direct, stoked). For my own conversations, match that energy. For anything that lands in `index.html` as user-facing copy, follow the dogsled brand voice (see `voice.md` and `anti-ai-tells.md`): direct, builder-grade, finance-literate, specific over general.

**Brand is locked.** The dogsled brand system is v1.3 and the decisions in `SKILL.md` section "Critical decisions baked into this system" are non-negotiable. Examples:

- Light is default (reading surface, not dashboard)
- Parchment is `#F2EAD8` (not trendy off-white)
- `pull hard`, not `push forward`
- Italic Fraunces at SOFT 60 for wordmarks, SOFT 100 only for display
- Ember-text variants for any text under 24px on parchment
- One italic phrase per heading (never italicize whole sentences)
- The mark uses `currentColor` (never hardcode its color)

If you find yourself wanting to violate one of these — surface it, explain why, and let me decide.

**Atmosphere is mandatory.** The topo lines and grain layer belong on every dogsled surface. Don't skip them when generating new pages or sections. They're what makes the brand feel like itself.

## What I'm probably asking for

- **Copy edits** to module names, descriptions, the hero, the tagline
- **Adding/removing modules** as the kit evolves
- **Swapping a module from Notes to Active** when it ships (with a new subdomain link)
- **New sections** (writing index, about, dogfood preview) — but each one needs to earn its place
- **Brand tweaks** (color, type, motion) that should propagate everywhere
- **Deploy help** (Vercel CLI, custom domain setup, OG image generation)

## What NOT to do

- Don't suggest a framework migration (Next.js, Astro, etc.) for this landing page. Single-file static HTML is the right choice for now. If the page outgrows that, *I'll* surface it.
- Don't add a newsletter signup, analytics, or "subscribe" CTAs until the content engine exists.
- Don't add stock-AI design tells: trendy gradients, neon accents, glassmorphism cards, generic "Get Started" CTAs, hero buttons with arrows. The brand has its own visual identity — use it.
- Don't reformat the module list into cards or a grid. The list-with-borders is intentional — it reads like a builder's log, not a marketing page.
- Don't replace the wordmark with a different lockup. The mark + `dogsled.dev` text combination is canonical.
- Don't change `pull hard` to anything else. That's the sled metaphor.
- Don't auto-fix "issues" you perceive without checking with me. Some choices look unfinished because they're deliberately spare.

## Starting a session

Tell me what we're doing. Examples:

- "Update the module copy" → check the `module-name` and `module-desc` text in `index.html`, propose changes, match brand voice
- "Add a new module" → add a new `<li>` to the module list following the existing pattern
- "Make module 03 live" → swap notes-only to linked, change pill, add href to its subdomain
- "Deploy to Vercel" → walk me through `vercel --prod` and domain setup
- "Add an OG image" → generate a Fraunces-based brand OG image, host as `og.png`, update meta tags

## The dogsled tagline (don't forget)

**Aim high. Pull hard. Leave tracks.** Three actions, three time horizons. Everything serves that philosophy.

Let's ship something.
