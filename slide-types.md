# Slide Types

Seven layout patterns. Each is a single `<section class="slide slide--TYPE">` block with predictable structure. Mix these across a deck for compositional variety.

## Type 1: hero

Full-viewport centered title. Use for the opening slide, mid-deck resets, and closers.

```html
<section class="slide slide--hero">
  <p class="hero__eyebrow reveal">brand.wordmark</p>
  <h1 class="slide__display reveal">The Big Title</h1>
  <p class="slide__subtitle reveal">Supporting one-liner that expands on the title.</p>
  <p class="hero__meta reveal">APRIL 2026 · LOCATION</p>
</section>
```

**Styling tips:**
- Center everything: `justify-content: center; align-items: center; text-align: center;`
- Background: `var(--hero-bg)`. Text: `var(--hero-text)`.
- Display size: `clamp(56px, 10vw, 128px)`, `font-weight: var(--display-weight)`, `letter-spacing: var(--letter-tight)`.
- Eyebrow (brand/wordmark) above the title in smaller muted type.
- Meta line below in `font-family: var(--font-mono); letter-spacing: 2.5px; text-transform: uppercase;` in `var(--hero-accent)`.

## Type 2: section-divider

Transition between major parts of the deck. Big title with optional tag and background flair.

```html
<section class="slide slide--divider">
  <div class="divider__tag reveal">LECTURE 2</div>
  <h1 class="slide__display reveal">Building the Thing</h1>
  <p class="slide__subtitle reveal">The shape of what we'll ship tonight.</p>
</section>
```

**Styling tips:**
- Same centered layout as hero, slightly less dramatic type (`clamp(48px, 8vw, 104px)`).
- A small pill tag ("LECTURE N" or "PART II") above the title in accent color.
- Optional: giant faded outline number in the background (`position: absolute; opacity: 0.08; font-size: 24vw;`).
- Consider a dramatic variant: full-bleed abstract SVG pattern or CSS gradient background.

## Type 3: content

The workhorse slide. Section label + heading + body (paragraph or bullets).

```html
<section class="slide slide--content">
  <div class="reveal">
    <div class="slide__label">Section Label</div>
    <h2 class="slide__heading">Your heading goes here</h2>
    <p class="slide__subheading">A short paragraph that expands on the heading in one or two sentences.</p>
  </div>
  <ul class="slide__bullets reveal">
    <li>Bullet point one</li>
    <li>Bullet point two</li>
    <li>Bullet point three</li>
  </ul>
</section>
```

**Styling tips:**
- Left-aligned. `justify-content: center;` but content is left-aligned within.
- Heading: `clamp(36px, 5.5vw, 76px); font-weight: var(--heading-weight);`.
- Label: small-caps mono type, 12–13px, letter-spacing 2.5px, color `var(--accent)`.
- Subheading: `clamp(18px, 2vw, 24px)`, `color: var(--text-dim)`, `max-width: 640px`.

## Type 4: cards

Multiple parallel items — facilitators, features, principles. Usually 2–4 cards.

```html
<section class="slide slide--cards">
  <div class="reveal">
    <div class="slide__label">Your Team</div>
    <h2 class="slide__heading">Three People, One Mission</h2>
  </div>
  <div class="cards-grid reveal">
    <article class="card">
      <div class="card__media"><!-- avatar, icon, or illustration --></div>
      <h3 class="card__title">Title</h3>
      <div class="card__badge">Role</div>
      <p class="card__body">Short bio or description.</p>
    </article>
    <!-- repeat 2–3 more times -->
  </div>
</section>
```

**Styling tips:**
- `display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: clamp(16px, 2vw, 32px);`.
- Cards: `background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius); padding: clamp(24px, 3vh, 40px);`.
- Badges: small pill `background: var(--accent); color: contrasting text; padding: 5px 12px; border-radius: 999px;`.
- Keep card count 2–4 for clarity; 5+ feels cluttered.

## Type 5: split

Two-column comparison. Before/after, problem/solution, now/future.

```html
<section class="slide slide--split">
  <div class="reveal">
    <div class="slide__label">Section Label</div>
    <h2 class="slide__heading">The Comparison</h2>
  </div>
  <div class="split-grid reveal">
    <div class="split-col split-col--a">
      <h3 class="split__title">Left Title</h3>
      <p class="split__body">Left-side body text.</p>
    </div>
    <div class="split-divider">
      <!-- optional center element: pill, icon, arrow, "TODAY" marker -->
    </div>
    <div class="split-col split-col--b">
      <h3 class="split__title">Right Title</h3>
      <p class="split__body">Right-side body text — usually the "after" / winning side.</p>
    </div>
  </div>
  <p class="split__footer reveal">Optional punchline below the comparison.</p>
</section>
```

**Styling tips:**
- `display: grid; grid-template-columns: 1fr auto 1fr; gap: clamp(24px, 3vw, 48px);`.
- Visually emphasize the "winning" side: border, background tint, stronger accent color.
- Center element is optional — can be a pill ("TODAY"), an arrow icon, or a subtle vertical divider line.
- On mobile (`max-width: 900px`), collapse to a single column stacked.

## Type 6: diagram

Visual flow or relationship map. Arrows, nodes, pipelines.

```html
<section class="slide slide--diagram">
  <div class="reveal">
    <div class="slide__label">The Flow</div>
    <h2 class="slide__heading">How It Works</h2>
  </div>
  <div class="flow reveal">
    <div class="flow__node">Input</div>
    <svg class="flow__arrow" viewBox="0 0 32 16"><path d="M2 8 L30 8 M22 2 L30 8 L22 14" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round"/></svg>
    <div class="flow__node">Process</div>
    <svg class="flow__arrow"><!-- same --></svg>
    <div class="flow__node">Output</div>
  </div>
  <p class="slide__caption reveal">Optional explanatory caption.</p>
</section>
```

**Styling tips:**
- For horizontal flow: `display: flex; align-items: center; gap: 16px; justify-content: center;` on `.flow`.
- Nodes: boxes or pill shapes with `background: var(--surface); border: 1.5px solid var(--accent);`.
- Arrows: inline SVG with `stroke: var(--accent)`.
- For richer diagrams (network, branching), use a full SVG with `viewBox="0 0 1200 560"`.

## Type 7: quote

Centered pull quote. Use sparingly — one or two per deck max.

```html
<section class="slide slide--quote">
  <div class="quote__mark reveal">"</div>
  <blockquote class="reveal">
    What we build, we teach. What we teach, we build better.
  </blockquote>
  <cite class="reveal">— attribution</cite>
</section>
```

**Styling tips:**
- Centered everything. Large serif/italic type for the quote: `clamp(28px, 4.5vw, 56px); font-style: italic; line-height: 1.3;`.
- Giant faded quote mark behind: `position: absolute; top: 10%; left: 8%; font-size: 20vw; opacity: 0.06; color: var(--accent);`.
- Citation in small-caps mono: `font-family: var(--font-mono); letter-spacing: 2px; text-transform: uppercase; margin-top: 32px;`.

## Markdown → slide type mapping

When parsing the source markdown, use this mapping:

| Markdown structure | Slide type |
|---|---|
| `:::hero` fence block | hero |
| `:::divider` fence block | section-divider |
| `:::content` fence block | content |
| `:::cards` fence block (plus nested `[Card]` markers) | cards |
| `:::split` fence block (with `left_*` and `right_*` keys) | split |
| `:::diagram` fence block (with a list of nodes) | diagram |
| `:::quote` fence block | quote |
| H1 alone on a slide (no body) | hero |
| H1 + 1-line body | section-divider |
| H2 + bullet list | content |
| Plain paragraph only | content |
| `> quoted block` alone | quote |

## Compositional variety (must follow)

Plan the deck sequence before writing HTML. Never:
- 3 hero/divider slides in a row
- 3 centered-content slides in a row
- 5+ slides with the same layout pattern back-to-back

Always:
- Start with hero
- Insert a section-divider between major content groups
- Intersperse split/diagram/cards with plain content
- End with hero, quote, or a strong CTA content slide
