# Example Presentation Source

This file demonstrates every slide type `fire-presentations` supports. Copy and adapt.

Three ways to input a slide:
1. **Plain markdown** — let the skill infer the type from structure (simplest).
2. **Fenced blocks** — explicit `:::type` fences for fine control (recommended).
3. **Mixed** — plain markdown for most slides, fences where you need specific layouts.

Slides are separated by `---` on its own line.

---

:::hero
eyebrow: brand.wordmark
title: Your Presentation Title
subtitle: A one-line subtitle that expands on the idea.
meta: APRIL 2026 · LOCATION
:::

---

:::divider
tag: PART ONE
title: The Problem
subtitle: What we're here to solve.
:::

---

:::content
label: Context
heading: The world changed

The market, the tooling, the expectations — everything accelerated last year. Your team needs a new playbook.

- Three workflows stopped working in 2024
- Two new constraints showed up this quarter
- One opportunity is closing fast
:::

---

:::cards
label: Who's on stage
heading: Your Facilitators

[Card]
title: Alex Gomez
badge: Host
body: 15 years shipping product at startups and platforms.

[Card]
title: Jordan Chen
badge: Instructor
body: Former staff engineer turned AI researcher.

[Card]
title: Sam Patel
badge: Guest
body: Built three companies around developer tools.
:::

---

:::split
label: Before / After
heading: The Shift

left_title: How it used to work
left_body: Planning meetings, spec documents, manual QA, slow releases. Every change took weeks.

divider: NOW

right_title: How it works tonight
right_body: You sketch the idea, AI scaffolds the code, you ship in an afternoon. Your role shifts from typing to directing.

footer: Tonight you cross that gap.
:::

---

:::diagram
label: The Flow
heading: Idea to Shipped in Five Steps

nodes: Idea | Brief | Generate | Review | Ship
caption: Each arrow is a feedback loop, not a waterfall.
:::

---

:::quote
text: The fastest code is the code you didn't have to write.
cite: Rich Hickey
:::

---

:::divider
tag: PART TWO
title: The Build
subtitle: Hands-on for the next 90 minutes.
:::

---

:::content
label: Setup
heading: Install the three tools

Before we start coding, get your environment ready:

- Install Claude Code (`npm install -g @anthropic-ai/claude-code`)
- Get an Anthropic API key from console.anthropic.com
- Clone the starter repo from the workshop URL

You have 5 minutes. Raise your hand if anything breaks.
:::

---

:::hero
eyebrow: That's a wrap
title: See you on Monday
subtitle: Ship something you built tonight.
meta: QUESTIONS WELCOME
:::
