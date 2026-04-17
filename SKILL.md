---
name: fire-presentations
description: Use when the user asks to create a presentation, slide deck, or workshop slides from a markdown file — generates a standalone scrolling HTML deck with hero/section/content layouts, keyboard nav, and a user-selected visual style
---

# Fire Presentations

Generate a single-file HTML slide deck from a markdown source. Scrolling, viewport-fit, zero build step, deployable anywhere.

## When the user invokes this skill, follow this workflow EXACTLY

### Step 1 — Locate the source markdown

If the user passed a file path as an argument, use it. Otherwise ask:
> Which markdown file should I use as the source? (e.g., `./presentation.md`)

If the file does not exist, offer to scaffold one from `example.md` in this skill's directory.

### Step 2 — Read and parse the markdown

Read the file. Use the convention in `slide-types.md` to detect slide boundaries and infer each slide's type. If the markdown uses plain structure (no explicit fenced blocks), infer:
- H1 alone on a slide → **hero**
- H1 + "LECTURE N" or similar → **section-divider**
- H2 + bullet list or short body → **content**
- Two columns separated by `||` or explicit left/right blocks → **split**
- Everything else → **content**

Count the total slides. This becomes the "X / Y" counter.

### Step 3 — Ask the user to pick a visual style

Present the 5 presets from `styles.md` verbatim in a numbered list, plus a custom option. Example phrasing:

> Pick a visual style for your deck:
> 1. **Brutalist Monochrome** — Stark black & white, Inter, sharp edges, industrial
> 2. **Editorial Serif** — Warm paper, Playfair Display, elegant magazine feel
> 3. **Terminal Retro** — Dark background, bright green JetBrains Mono, retro-futuristic
> 4. **Sunset Magazine** — Warm peach/coral gradients, Instrument Serif, vibrant
> 5. **Midnight Galaxy** — Deep violet/indigo, Space Grotesk, glowing accents
> 6. **Custom** — describe your own colors and typography

Wait for the user's selection.

### Step 4 — Confirm output path and tone

Default output path: `./slides/<source-basename>.html`. Ask:
> I'll save to `<default path>`. OK, or pick another location?

Optionally also ask about tone/density (default: balanced):
> Any tone preference? (e.g., "technical", "playful", "formal" — or skip)

### Step 5 — Generate the HTML

Write ONE self-contained HTML file using:
- The base engine structure from `template.html`
- The chosen style preset's CSS variables from `styles.md`
- Per-slide layouts from `slide-types.md`

**Non-negotiable engine requirements:**
- `scroll-snap-type: y mandatory` on `.deck`, `scroll-snap-align: start` on each `.slide`
- Each slide exactly `100dvh` tall
- Keyboard nav: ←/→/Space/PgUp/PgDn/Home/End
- IntersectionObserver-driven `.visible` class for reveal animations
- Side nav dots (current slide = accent color)
- "N / total" counter (bottom-left or bottom-right per style)
- `@media (prefers-reduced-motion: reduce)` disables animations
- Responsive: single-column on `max-width: 900px`
- Only Google Fonts as external dep — nothing else

**Slide composition rules:**
- Vary layouts across consecutive slides — never three hero slides in a row, never three centered-content slides in a row. Alternate centered / left-heavy / split / full-bleed.
- At least one section-divider between major content groups.
- Hero and section-divider slides use full-bleed backgrounds (gradients or large display type).
- Content slides have breathable padding (`clamp(40px, 6vh, 80px) clamp(60px, 8vw, 120px)`).

### Step 6 — Preview and report

If the Puppeteer MCP is available in the current session:
1. Navigate to `file://<output path>`
2. Screenshot slide 1 (the hero)
3. Scroll to a middle content slide and screenshot
4. Scroll to the last slide and screenshot

Report the output path and a one-line summary (slide count, style used).

If Puppeteer is not available, just report the path and suggest: `open <path>`.

## Supporting Files

- `styles.md` — 5 distinct style presets with full CSS variable blocks
- `slide-types.md` — Layout patterns and HTML fragments for each slide type
- `template.html` — Base engine scaffold (JS + scroll-snap + chrome)
- `example.md` — Sample markdown input demonstrating all slide types

## Red Flags — Stop and ask

- Markdown has fewer than 3 slides → ask if the user really wants a deck
- No title/H1 anywhere → ask for a title
- User picks Terminal Retro but wants a serif display font → clarify which wins
- The markdown contains code blocks → confirm the style preset supports code (Terminal Retro and Brutalist do; Editorial Serif and Sunset Magazine need mono font added)

## Common Mistakes

| Mistake | Fix |
|---|---|
| Writing a React/Next.js app | Single HTML file only. No build step. |
| Using PPTX-style fixed 1920×1080 slides | Use `100dvh` + `clamp()` everywhere. |
| Hard-coding colors instead of CSS variables | All colors come from the chosen preset's `:root` block. |
| Omitting the keyboard nav JS | Copy the full SlideEngine from `template.html` verbatim. |
| Adding heavy JS libraries | Vanilla JS only. No React, no build step. |
| Skipping the accessibility fallback | `prefers-reduced-motion` MUST disable all animations. |
