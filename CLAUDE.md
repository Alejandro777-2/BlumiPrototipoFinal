# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-file clickable prototype (v1, "vertical slice") for pitching **Blumi** — a streak/loyalty gamification feature planned for the Atlas × Diners Club **blu** banking app in Ecuador. No build system, no dependencies, no server required.

## Running the prototype

Open `index.html` directly in any browser. There is no build step, no `npm install`, and no dev server.

## Architecture

Everything lives in one file: `index.html`. It contains:

- **Embedded CSS** — a full design system defined via `:root` CSS custom properties (palette, typography), followed by per-screen and per-component styles.
- **7 HTML screens** — each is a `<section class="screen">` inside a `.phone` div that simulates an iPhone frame. Only one screen is visible at a time via the `.active` class.
- **A demo switcher bar** below the phone frame — lets a presenter jump between any screen during a pitch.
- **One JS function** — `go(id)` toggles `.active` on screens and the corresponding demo-switch button, then resets scroll to top.

The two assets (`assets/blumi-feliz.png`, `assets/blumi-triste.png`) are the Blumi character images. SVG placeholder definitions for Blumi also exist inline (inside a `<defs>` block) and are used by screens that haven't swapped in the real PNGs yet.

## Screens

| ID | Content |
|----|---------|
| `screen-home` | Entry point — mimics the blu host app (light chrome, Diners card, bottom nav) with the Blumi card as the new feature entry point |
| `screen-racha` | Active streak — the main "money shot" for the pitch |
| `screen-rota` | Broken streak — emotional hook; `filter:saturate(.7)` dims the whole screen; sad Blumi image |
| `screen-progreso` | Weekly progress history |
| `screen-mantenida` | Streak-maintained celebration screen |
| `screen-canje` | Rewards catalog |
| `screen-nivel` | Level / multiplier screen (tiers: Chispa → Brasa → Llama Azul → Fogata → Incendio) |

## Design system

Defined in `:root`:

```
--navy / --navy-2   dark blues (Diners brand authority)
--cyan / --cyan-lt  electric blue (Blumi's "blue fire")
--cream / --warm    neutral / warm accent
--font-display      Space Grotesk (headings)
--font-body         Inter (body text)
```

All colors, glow effects, and animations reference these variables — edit them there to restyle the whole prototype.

## Blumi character states

- `.blumi.is-lit` — happy state, `float` animation, cyan drop-shadow, `.halo` glow behind it.
- `.blumi.is-out` — sad state, `float-sad` animation (slower, slight tilt), no halo, `filter:saturate(.7)` on parent screen.

Comments throughout the file mark where to swap SVG placeholders for final artwork from Flow: look for `▼▼ BLUMI placeholder`.
