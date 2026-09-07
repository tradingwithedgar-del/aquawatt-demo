---
version: alpha
name: RALLY-design-system
description: An editorial product landing page built on a single deep-cobalt field, warm paper neutrals, and one gold accent that only ever appears on dark. Archivo variable-width headlines set tight and heavy against Instrument Sans body copy. Corners are effectively square (2px on buttons, 0 everywhere else), elevation is absent from chrome and reserved entirely for product photography, and the page's one piece of spectacle is a 48-frame bottle that rolls across the viewport as the scrollbar moves.

colors:
  primary: "#1B3C96"
  ink: "#0B1739"
  paper: "#F7F5F0"
  warm: "#EFEBE2"
  gold: "#E0A02E"
  gold-lift: "#F0B84A"
  mist: "#56658A"
  rust: "#B03427"
  hairline: "rgba(11,23,57,0.14)"
  body-on-cobalt: "#EAF0FC"
  body-on-photo: "#D3DBEE"
  body-on-ink: "#9EABC8"
  link-on-ink: "#C6D0E6"
  legal-on-ink: "#8B99B8"
  placeholder: "#5F6C8C"
  scrim-near: "rgba(6,12,32,0.86)"
  scrim-mid: "rgba(6,12,32,0.62)"
  scrim-far: "rgba(6,12,32,0.30)"
  header-glass-light: "rgba(247,245,240,0.92)"
  header-glass-dark: "rgba(9,18,44,0.74)"

typography:
  hero-display:
    fontFamily: "Archivo, 'Instrument Sans', sans-serif"
    fontSize: "clamp(42px, 5.4vw, 80px)"
    fontWeight: 900
    fontVariationSettings: "'wdth' 118"
    lineHeight: 0.96
    letterSpacing: "-0.028em"
  section-display:
    fontFamily: "Archivo, 'Instrument Sans', sans-serif"
    fontSize: "clamp(32px, 5vw, 60px)"
    fontWeight: 800
    fontVariationSettings: "'wdth' 112"
    lineHeight: 0.96
    letterSpacing: "-0.028em"
  chapter-display:
    fontFamily: "Archivo, 'Instrument Sans', sans-serif"
    fontSize: "clamp(30px, 4vw, 52px)"
    fontWeight: 800
    fontVariationSettings: "'wdth' 112"
    lineHeight: 0.96
    letterSpacing: "-0.028em"
  wordmark:
    fontFamily: "Archivo, sans-serif"
    fontSize: 22px
    fontWeight: 900
    fontVariationSettings: "'wdth' 118"
    letterSpacing: "0.09em"
  body:
    fontFamily: "'Instrument Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    fontSize: 17px
    fontWeight: 400
    lineHeight: 1.6
  lead:
    fontFamily: "'Instrument Sans', sans-serif"
    fontSize: "clamp(16.5px, 1.5vw, 19px)"
    lineHeight: 1.6
  eyebrow:
    fontFamily: "Archivo, sans-serif"
    fontSize: 12px
    fontWeight: 700
    fontVariationSettings: "'wdth' 100"
    letterSpacing: "0.18em"
    textTransform: uppercase
  label:
    fontFamily: "Archivo, sans-serif"
    fontSize: 11.5px
    fontWeight: 700
    letterSpacing: "0.15em"
    textTransform: uppercase
  button:
    fontFamily: "Archivo, sans-serif"
    fontSize: 15px
    fontWeight: 700
    fontVariationSettings: "'wdth' 104"

rounded:
  none: 0
  button: 2px

spacing:
  shell: "min(1200px, 100% - 48px)"
  shell-narrow: "min(1200px, 100% - 34px)"
  section: "clamp(84px, 11vw, 140px)"
  chapter: "12vh"
  footer: "clamp(72px, 9vw, 120px)"
  measure-body: "40ch"
  measure-lead: "46ch"
  measure-headline: "18ch"

components:
  demo-banner: "Full-width ink bar, 13px, gold-lift bold inline emphasis. Declares the page a concept demo."
  header: "Fixed, 70px, three states — transparent, .stuck (paper glass), .stuck.dark (ink glass)."
  roller: "Fixed 48-frame canvas sequence, scroll-position-driven, drop-shadowed, pointer-events none."
  hero: "100svh two-column cobalt field, 1.06fr / .94fr, copy left and bottle right."
  chapter: "96svh full-bleed photograph with a directional scrim, alternating sides via .flip."
  spec-grid: "auto-fit dl on a hairline background, 1px gaps rendering as rules."
  notify-form: "Underline-only inputs, uppercase labels, inline status paragraph."
  aside-slot: "Warm block under a 1.5px ink rule, holds the secondary ask."
  footer: "70svh ink field, 1.5fr/1fr/1fr, gold-lift column headings."
---

## Overview

RALLY is a single-product launch page that behaves like an editorial feature rather than a store. The structure is a **pulse between a saturated cobalt field, four full-bleed photographic chapters, and warm paper utility sections** — the background color change *is* the section divider. There are no cards, no rounded containers, no decorative gradients, and no shadows anywhere on interface chrome. The only elevation in the entire system sits under product photography.

Density is deliberately low. The hero and each story chapter occupy roughly a full viewport, and copy is held to a 40–46 character measure regardless of how wide the shell gets. The page earns its length through photography and one continuous piece of motion, not through stacked components.

That motion is the system's signature: a bottle rendered as 48 frames rolls left-to-right across the viewport, and the frame shown is derived purely from scroll position. The scrollbar is the animation's only input. It is fixed-position, non-interactive, and disappears entirely under `prefers-reduced-motion`.

**Key characteristics:**

- One brand color (`{colors.primary}` cobalt) and one accent (`{colors.gold-lift}`) that appears **only on dark surfaces** — never on paper.
- Square by default. `{rounded.button}` is 2px; every other corner is 0.
- Archivo variable-width headlines, always heavy (800–900), always tight (`-0.028em`, line-height 0.96), with width axis pushed to 112–118.
- Alternating full-bleed sections — cobalt → photograph → photograph → paper → warm → ink — where the color shift replaces any border or divider.
- Zero chrome shadows. Two drop-shadows total, both under bottle imagery.
- Hairline rules and 1px grid gaps do the work that borders and cards do elsewhere.
- Reveals are uniform: 24px rise, 0.8s, staggered in 80ms steps. Nothing scales, nothing bounces.

## Colors

### Brand

- **Cobalt** (`{colors.primary}` — #1B3C96): The hero field, every primary button, every form label, and the wordmark once the header sticks over light. This is the page's structural color, not a highlight — it is used at full-bleed scale.
- **Ink** (`{colors.ink}` — #0B1739): Body text on light surfaces, the footer field, and button hover. A deep navy rather than black, so it reads as the same family as cobalt.

### Accent

- **Gold Lift** (`{colors.gold-lift}` — #F0B84A): Eyebrows, the emphasized half of the hero headline, the 64px rule under each chapter, and footer column headings. **As a text or rule accent it appears only on cobalt, photography, or ink** — it lacks the contrast to sit on paper. Its one light-surface use is as a *fill* (the pale button's hover), where ink text sits on top of it.
- **Gold** (`{colors.gold}` — #E0A02E): The deeper sibling, reserved for physical-product references (the bottle's cap) rather than interface.

### Surface

- **Paper** (`{colors.paper}` — #F7F5F0): The default canvas. Warm off-white, never pure.
- **Warm** (`{colors.warm}` — #EFEBE2): One step deeper. Used for the spec section, the aside slot, and the form's status message — the "recessed" tone that signals supporting content.

### Text

- **Mist** (`{colors.mist}` — #56658A): Secondary copy on light surfaces. Leads, spec definitions, form notes.
- **On cobalt** (`{colors.body-on-cobalt}` — #EAF0FC), **on photography** (`{colors.body-on-photo}` — #D3DBEE), **on ink** (`{colors.body-on-ink}` — #9EABC8): Three separate tints of near-white, each tuned to its own background. Do not substitute one for another — pure white is never used for body copy.
- **Placeholder** (`{colors.placeholder}` — #5F6C8C): Input placeholders only.

### Utility

- **Rust** (`{colors.rust}` — #B03427): Used **exclusively** for the focus ring and the form status message's left border. It is the page's only warm-red and carries no decorative role. Do not extend it into badges or hover states.
- **Hairline** (`{colors.hairline}` — rgba(11,23,57,0.14)): Input underlines and the spec grid's background, showing through 1px gaps as rules.

### Scrims

Chapter photography carries a **directional** gradient, not a flat overlay: `{colors.scrim-near}` → `{colors.scrim-mid}` at 46% → `{colors.scrim-far}`. It runs left-to-right on standard chapters and is reversed (270deg) on `.flip`, so the dark end always sits under the text. Below 760px both variants become a top-to-bottom scrim instead, since the copy is no longer beside the image.

**No decorative gradients exist.** The scrims are legibility infrastructure.

## Typography

### Families

- **Display**: `Archivo` — a variable font on both width (100–125) and weight (500–900). The width axis is doing real work here: 118 for the wordmark and hero, 112 for section headings, 104 for buttons, 100 for eyebrows. Narrower as the type gets smaller.
- **Body**: `Instrument Sans` at 400/500/600.

### Rules

- Headlines are **always** 800 or 900, line-height 0.96, letter-spacing `-0.028em`, with `text-wrap: balance`. Never set a headline at a lighter weight or looser tracking.
- Every heading size is a `clamp()` — there are no fixed headline sizes.
- Two uppercase micro-styles carry all the labeling: `{typography.eyebrow}` at 0.18em tracking above headings, and `{typography.label}` at 0.15em for form labels and footer column headings. Both are Archivo, never Instrument Sans.
- Body copy is 17px/1.6 and constrained to `{spacing.measure-body}` or `{spacing.measure-lead}`. Headlines cap at `{spacing.measure-headline}`.
- `<em>` inside a headline is **not italic** — it is reset to normal style and recolored `{colors.gold-lift}`. This is the emphasis mechanism.

## Layout

The single container is `.shell` at `{spacing.shell}`, tightening to `{spacing.shell-narrow}` below 760px. Everything centers on it; nothing else sets its own max-width.

Sections are viewport-scale: hero at `100svh`, chapters at `96svh`, footer at `70svh`. Utility sections use `{spacing.section}` vertical padding instead.

Two asymmetric grids appear, both close to but deliberately not 50/50 — `1.06fr .94fr` for the hero and `1.02fr .98fr` for the buy section. The footer runs `1.5fr 1fr 1fr`.

**Breakpoints:**
- `980px` — hero and buy collapse to one column; footer becomes 2-up with the brand block spanning full width.
- `760px` — shell tightens, nav links hide (the CTA persists and pushes right), the roller narrows to 62vw, chapter boxes drop their max-width, and scrims rotate to vertical.

## Components

### Buttons

Four variants, all sharing `{rounded.button}`, 50px minimum height, and `{typography.button}`:

| Variant | Fill | Text | Hover |
|---|---|---|---|
| `.btn` | `{colors.primary}` | paper | fills `{colors.ink}` |
| `.btn.pale` | paper | `{colors.primary}` | fills `{colors.gold-lift}`, text to ink |
| `.btn.line` | transparent, 50% white border | paper | 14% white wash |
| `.btn.ink` | transparent, cobalt border | `{colors.primary}` | inverts to cobalt fill |

Borders are 1.5px. Transitions are 0.2s on color properties only — buttons never move, scale, or lift.

### Header

Fixed, 70px, and repaints from scroll position into one of three states: transparent over the hero, `.stuck` (paper glass, `blur(12px) saturate(150%)`, hairline border) over light sections, and `.stuck.dark` (ink glass) when a dark section spans the header's y-position. State is computed from the story and footer bounding rects, not from a scroll threshold alone.

### Spec grid

A `<dl>` on a `{colors.hairline}` background with `gap: 1px`, `auto-fit` at `minmax(212px, 1fr)`, each cell filled `{colors.warm}`. The background shows through the gaps as hairline rules, so the grid reflows at any column count without border-collapse problems. This is the pattern to reuse for any tabular content — not bordered cards.

### Form

Inputs are **underline-only**: no fill, no box, no radius, 1.5px bottom border that goes cobalt on hover and focus. 54px minimum height. Labels are uppercase `{typography.label}` in cobalt above each field. Validation is inline via a single `role="status"` paragraph on `{colors.warm}` with a 2px `{colors.rust}` left border.

## Motion

- **Reveal** (`.rise`): 24px translate plus opacity, 0.8s, `cubic-bezier(.2,.7,.3,1)`, triggered by IntersectionObserver at 15% with a `-12%` bottom margin, unobserved after firing. Stagger via `.d1`/`.d2`/`.d3` at 80/160/240ms.
- **Rule**: `scaleX(0)` → 1 from the left, 0.7s, 150ms after its parent reveals.
- **Roller**: 48 frames × 5 rotations mapped onto total scroll progress. Horizontal travel is smoothstep-eased across the viewport; vertical travel is linear with a settle toward its resting position as the footer enters. Painted in `requestAnimationFrame`, skipping redundant frames.

Nothing loops, nothing autoplays, nothing animates on hover except color.

## Accessibility

These are load-bearing and must survive any redesign:

- Focus ring is `3px solid {colors.rust}` at `3px` offset on all interactive elements via `:focus-visible`.
- Minimum tap targets: 44px on nav links and footer links, 50px on buttons, 54px on inputs.
- `prefers-reduced-motion` collapses all transitions to 0.001ms, **un-fixes the roller** into a static centered image, and forces every `.rise` and `.rule` to its final state. The page must remain complete with zero motion.
- Every chapter photograph has descriptive alt text, and the roller canvas is `aria-hidden`.
- Photography failure is designed for: a broken image swaps to a diagonal-stripe placeholder rather than collapsing the layout.

## What this system does not do

- No rounded cards, no border-radius above 2px.
- No shadows on buttons, headers, inputs, or containers.
- No decorative gradients — gradients are scrims only.
- No pure white and no pure black.
- No gold on paper.
- No second accent color. If something needs to stand out on a light surface, it becomes cobalt or it becomes larger.
