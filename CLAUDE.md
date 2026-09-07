# aquawatt-demo

A concept demo landing page built by Grand Nash Studio for **RALLY**, a king coconut
water brand. Static HTML, no build step, no framework, no package manager for the
page itself.

## Layout

| Path | What it is |
|---|---|
| `index.html` | **The page.** 460 lines — markup, styles and behaviour in one file. This is canonical. |
| `DESIGN.md` | The visual contract. Read it before any UI change. |
| `rally/img/`, `rally/frames/` | Assets the root page loads: the bottle shot and 48 roll frames. |
| `rally/index.html` | Superseded earlier build (602 lines, uses anime.js). Not the live page. |
| `rally/artifact.html` | Generated wrapper copy of `rally/index.html`. Never hand-edit. |
| `rally/UPDATING.md` | Plain-language edit guide written for the client, not for agents. |

Edit `index.html`. Touch `rally/` only for assets, and only say you have changed
"the page" when you changed the root file.

## DESIGN.md is the authority

`DESIGN.md` documents this project's actual design system, derived from the CSS in
`index.html`. When a design decision comes up, it wins over any general design skill
and over your own instincts. Its "What this system does not do" section is a list of
hard constraints — square corners, no chrome shadows, no decorative gradients, no
pure white or black, no gold on paper, one accent color.

If a change genuinely needs to break one of those rules, say so and get agreement
first. Do not quietly widen the system.

Keep `DESIGN.md` current: if you change a token or add a component pattern in
`index.html`, update `DESIGN.md` in the same change.

## Which design skill to use

This repo has a lot of installed design skills and several contradict each other
outright — one mandates GSAP scroll-pinning and heavy motion, another bans gradients
and shadows. Do not let them fight.

- **Default for UI work here: none of them.** `DESIGN.md` already specifies this
  project. Reach for a skill only when the task is genuinely open-ended.
- `redesign-existing-projects` — the one to use if asked for a broad redesign pass,
  because it audits before it changes things. Still subordinate to `DESIGN.md`.
- `gpt-taste`, `high-end-visual-design`, `minimalist-ui`, `industrial-brutalist-ui`,
  `stitch-design-taste`, `design-taste-frontend-v1` — **do not fire these on this
  repo.** They impose their own visual language, which is precisely what `DESIGN.md`
  exists to prevent. They are here for other projects.
- `full-output-enforcement` — leave off unless asked. It bans truncation globally and
  makes every response much longer.
- Image-generation skills (`imagegen-frontend-web`, `imagegen-frontend-mobile`,
  `brandkit`, `image-to-code`) — only on explicit request. They cost real money.

The Vercel skills (`vercel-react-*`, `vercel-composition-patterns`) target React and
Next.js. This project is vanilla HTML, so they should stay quiet.

## Reviewing before something goes to a client

`grand-nash-outreach` owns pre-send review — accessibility, privacy, compliance,
"is this safe to launch". It is an account-level skill, so it travels outside this
repo. Use it, not a general UI-audit skill, when Edgar asks whether something is
ready to send.

## Demo-site guardrails

This page is a pitch artifact, not a live store. Preserve all of these:

- The `.demo` banner declaring it a concept demo with an unconnected form.
- `<meta name="robots" content="noindex, nofollow">`.
- The signup form is front-end only. It must never be wired to a real endpoint or
  collect data anywhere.
- Do not invent stockists, press quotes, testimonials, certifications or launch
  dates. The "Stockists" copy deliberately says the list is empty; that honesty is
  the point.
- Photography is AI-generated stand-in imagery, not real product shots. Do not
  present it as real. See `rally/UPDATING.md`.

## Accessibility is load-bearing

`DESIGN.md` lists these in full. The ones easiest to break by accident:

- `:focus-visible` ring — `3px solid #B03427` at `3px` offset.
- Tap targets — 44px nav and footer links, 50px buttons, 54px inputs.
- `prefers-reduced-motion` un-fixes the rolling bottle into a static centered image
  and forces every reveal to its final state. **The page must be complete with zero
  motion.** Test this whenever you touch the scroll code.

## Checking your work in a browser

`playwright-cli` is installed and is the way to actually look at the page:

```bash
python3 -m http.server 8899 &
playwright-cli open && playwright-cli resize 1440 900
playwright-cli goto http://localhost:8899/
playwright-cli screenshot
playwright-cli close
```

In a Claude Code cloud session the browser needs configuring first — copy
`.playwright/cli.config.example.json` to `.playwright/cli.config.json`. The CDN it
would otherwise download from is blocked, and the container runs as root, so the
config points at the image's Chromium and disables the sandbox. Local machines need
none of this.

Expect four console errors in a cloud session — Google Fonts and the CloudFront
images are blocked by the egress policy, plus a missing `favicon.ico`. Those are
environment artifacts, not page bugs. Fonts falling back to Helvetica also makes
headlines wrap wider than they will in reality, so do not chase layout ghosts from
a cloud screenshot.

## Known issues

- No favicon — `/favicon.ico` 404s.
- At scroll position 0 the rolling bottle overlaps the RALLY wordmark in the header.
  May be intentional as an entry state; unconfirmed.
- Photography loads from a temporary CloudFront URL that will eventually break.
  `rally/UPDATING.md` explains bringing it local.

## Conventions

- No build step. Do not add a bundler, framework or CSS preprocessor.
- Styles live in the `<style>` block in `index.html`; behaviour in the `<script>`
  block at the bottom. Keep it that way — one file is the point.
- Vanilla JS in an IIFE, `"use strict"`, `var`, feature-detected. Match it.
- Do not commit secrets. `.env` and `.playwright/` are ignored.
