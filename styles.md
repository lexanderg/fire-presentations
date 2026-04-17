# Style Presets

Five drop-in style presets. Each is a complete CSS variable block + font import. Pick one, paste into the template's `:root`, and every slide picks up the look.

Every preset provides:
- `--bg` — base background
- `--surface` — card/elevated surface
- `--text` — primary text
- `--text-dim` — secondary text
- `--accent` — primary accent (labels, active dot)
- `--accent-2` — secondary accent (quotes, badges)
- `--border` — subtle dividers
- `--hero-bg` — dramatic background for hero/divider slides (can be gradient)
- `--font-display` — for big display headings
- `--font-body` — for body text
- `--font-mono` — for code or small-caps labels

---

## 1. Brutalist Monochrome

**Vibe:** industrial, uncompromising, editorial. Think Kanye album cover meets Swiss design manual.
**Best for:** technical keynotes, research talks, manifesto-style decks.
**Font pairing:** Inter (display + body) + JetBrains Mono (labels).

```css
/* <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800;900&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet"> */
:root {
  --bg: #F4F4F2;
  --surface: #FFFFFF;
  --surface-2: #E8E8E4;
  --text: #0A0A0A;
  --text-dim: #555555;
  --accent: #0A0A0A;
  --accent-2: #FF3B30;
  --border: rgba(10, 10, 10, 0.12);
  --hero-bg: #0A0A0A;
  --hero-text: #F4F4F2;
  --hero-accent: #FF3B30;
  --font-display: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-body: 'Inter', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --display-weight: 900;
  --heading-weight: 800;
  --body-weight: 400;
  --letter-tight: -3px;
  --radius: 0;
}
```

**Hero slide treatment:** black bg, cream text, red accent line. Display text is `clamp(56px, 11vw, 140px)`, weight 900, letter-spacing -3px. No rounded corners anywhere.

---

## 2. Editorial Serif

**Vibe:** printed magazine, thoughtful, warm. Think *The New Yorker* crossed with a design journal.
**Best for:** essays, storytelling, design reviews, research summaries.
**Font pairing:** Playfair Display (display) + Inter (body) + JetBrains Mono (labels).

```css
/* <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@500&display=swap" rel="stylesheet"> */
:root {
  --bg: #FAF6EE;
  --surface: #FFFFFF;
  --surface-2: #F1ECE0;
  --text: #1A1714;
  --text-dim: #6B645A;
  --accent: #A0522D;       /* sienna */
  --accent-2: #3E5C4A;     /* forest */
  --border: rgba(26, 23, 20, 0.12);
  --hero-bg: radial-gradient(ellipse at 30% 40%, #F5EBD6 0%, #EADFC4 60%, #D9CAA8 100%);
  --hero-text: #1A1714;
  --hero-accent: #A0522D;
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body: 'Inter', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --display-weight: 900;
  --heading-weight: 700;
  --body-weight: 400;
  --letter-tight: -1px;
  --radius: 12px;
}
```

**Hero slide treatment:** warm cream gradient bg, serif display italic for drama (`font-style: italic` on an accent word). Use small-caps JetBrains Mono for metadata.

---

## 3. Terminal Retro

**Vibe:** CRT monitor, hacker console, retro-futuristic. Think *Mr. Robot* title cards.
**Best for:** CLI tools, systems talks, security research, dev tooling.
**Font pairing:** JetBrains Mono everywhere + Space Grotesk for the occasional display hit.

```css
/* <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700;800&family=Space+Grotesk:wght@600;700&display=swap" rel="stylesheet"> */
:root {
  --bg: #0B0F0A;
  --surface: #121A10;
  --surface-2: #1A2418;
  --text: #C7F284;
  --text-dim: #7A9A5C;
  --accent: #9BFF3C;
  --accent-2: #FFB84D;     /* amber glow */
  --border: rgba(155, 255, 60, 0.15);
  --hero-bg: radial-gradient(ellipse at 50% 60%, #0F1D0B 0%, #070B06 100%);
  --hero-text: #C7F284;
  --hero-accent: #9BFF3C;
  --font-display: 'Space Grotesk', 'JetBrains Mono', monospace;
  --font-body: 'JetBrains Mono', monospace;
  --font-mono: 'JetBrains Mono', monospace;
  --display-weight: 700;
  --heading-weight: 700;
  --body-weight: 400;
  --letter-tight: -1px;
  --radius: 4px;
  --glow: 0 0 24px rgba(155, 255, 60, 0.35);
}
```

**Hero slide treatment:** dark green-black bg. Display heading gets `text-shadow: 0 0 12px var(--accent);`. Blinking cursor `▊` at end of title (CSS animation). Scanline overlay via `background-image: repeating-linear-gradient(0deg, rgba(155,255,60,0.02) 0, rgba(155,255,60,0.02) 1px, transparent 1px, transparent 3px);` on hero.

---

## 4. Sunset Magazine

**Vibe:** warm, generous, optimistic. Think Kinfolk meets a late summer evening.
**Best for:** lifestyle, product pitches, brand presentations, creative workshops.
**Font pairing:** Instrument Serif (display) + Inter (body) + JetBrains Mono (labels).

```css
/* <link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@500;600&display=swap" rel="stylesheet"> */
:root {
  --bg: #FFF0E6;
  --surface: #FFFFFF;
  --surface-2: #FFE3D1;
  --text: #3A1A0F;
  --text-dim: #8A5B4B;
  --accent: #E85D2C;       /* coral */
  --accent-2: #D4A373;     /* sand */
  --border: rgba(58, 26, 15, 0.10);
  --hero-bg: linear-gradient(135deg, #FFB88C 0%, #F26B5A 45%, #A8325E 100%);
  --hero-text: #FFFFFF;
  --hero-accent: #FFE3D1;
  --font-display: 'Instrument Serif', Georgia, serif;
  --font-body: 'Inter', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --display-weight: 400;
  --heading-weight: 400;
  --body-weight: 400;
  --letter-tight: -1.5px;
  --radius: 20px;
}
```

**Hero slide treatment:** warm coral-to-magenta gradient bg. Display heading uses `Instrument Serif` with occasional italic word for expressive contrast. Generous padding. Soft round corners (`--radius: 20px`) everywhere.

---

## 5. Midnight Galaxy

**Vibe:** ambient, futuristic, contemplative. Think space telescope imagery meets synth-wave.
**Best for:** AI/ML talks, vision decks, launch keynotes, futurist themes.
**Font pairing:** Space Grotesk (display + body) + JetBrains Mono (labels).

```css
/* <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@500;600&display=swap" rel="stylesheet"> */
:root {
  --bg: #0A0318;
  --surface: #160D2E;
  --surface-2: #22164A;
  --text: #F0EBFF;
  --text-dim: #A89DC4;
  --accent: #B794F4;       /* lavender */
  --accent-2: #38E1FF;     /* cyan */
  --border: rgba(183, 148, 244, 0.15);
  --hero-bg: radial-gradient(ellipse at 30% 20%, #3D2176 0%, #1B0C3F 40%, #0A0318 85%);
  --hero-text: #F0EBFF;
  --hero-accent: #B794F4;
  --font-display: 'Space Grotesk', -apple-system, sans-serif;
  --font-body: 'Space Grotesk', sans-serif;
  --font-mono: 'JetBrains Mono', monospace;
  --display-weight: 700;
  --heading-weight: 600;
  --body-weight: 400;
  --letter-tight: -2px;
  --radius: 16px;
  --glow: 0 0 40px rgba(183, 148, 244, 0.25);
}
```

**Hero slide treatment:** deep violet radial gradient. Accent text gets glow (`text-shadow: 0 0 28px var(--accent)`). Scatter tiny white dots (stars) via inline SVG in the hero background. Cards use subtle backdrop-filter blur.

---

## Applying a preset

In the generated HTML:
1. Paste the preset's `<link>` for Google Fonts into `<head>`.
2. Paste the `:root` block into the stylesheet.
3. Map structural CSS to variables:
   - `.deck` → `background: var(--bg); color: var(--text);`
   - `.slide--hero` / `.slide--divider` → `background: var(--hero-bg); color: var(--hero-text);`
   - `.slide__display` → `font-family: var(--font-display); font-weight: var(--display-weight); letter-spacing: var(--letter-tight);`
   - `.slide__label` → `font-family: var(--font-mono); color: var(--accent);`
   - cards/badges → `background: var(--surface); border: 1px solid var(--border); border-radius: var(--radius);`

## Custom palette

If the user asks for a custom style, fill in the same 11 variables by asking:
1. Primary background color (hex)?
2. Text color (hex)?
3. Accent color (hex)?
4. Serif, sans-serif, or monospace feel?
5. Sharp (radius 0), soft (radius 12px+), or medium (radius 4-8px) corners?

Then generate a new `:root` block and a matching `--hero-bg` (radial gradient from accent to bg).
