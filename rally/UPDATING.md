# RALLY landing page — how to make content updates

Three files, no build step, no framework:

| File | What it is |
|---|---|
| `index.html` | The whole page: markup, styles and behaviour |
| `anime.umd.min.js` | The animation library (anime.js v4.5.0, MIT licence) |
| `artifact.html` | A generated copy for hosts that supply their own page wrapper. Do not edit it by hand — it is rebuilt from `index.html` |

Open `index.html` in any text editor, change the text, save, re-upload.

## Do this first: bring the photography local

The images are currently loaded from a temporary CDN. That is fine for review and
will break eventually. Download the five files, put them in `rally/img/`, and change
one line near the bottom of `index.html`:

```js
var BASE = "img/";
```

Then rename the downloads to match the names in `SHOTS` on the lines below it, or
change those names to whatever you saved them as. Nothing else has to change.

**These are generated stand-ins, not real product photography.** They approximate the
bottle but the label will not match yours exactly. Replace them with your own shots
before launch — the layout is built to take them at the same crops:

| Slot | Crop | What it shows |
|---|---|---|
| `hero` | 3:2 landscape | The bottle on a plain studio backdrop. Fills the right half of the hero |
| `bottle` | 4:5 portrait | The bottle straight on. Travels down the page inside a framed panel |
| `coconuts` | 4:3 landscape | King coconuts, one cut open |
| `plantation` | 16:9 landscape | The growing region |
| `pour` | 4:5 portrait | Coconut water poured into a glass |

If a photo fails to load the page shows a labelled panel in its place rather than a
broken image, so a missing file is obvious instead of ugly.

## The four story panels

Search for `<div class="beat"`. Each has an eyebrow, a heading and one or two
paragraphs. Edit the words between the tags and leave the tags alone.

The scroll choreography is built from the number of panels, so if you add or remove
one, the timeline adjusts on its own — but also add or remove a `<span></span>` in
`<div class="dots">` so the progress dots still match.

Which photo sits behind which panel is set by one line:

```js
var plateShots = ["coconuts","pour","hero","plantation"];
```

Reorder that array to reorder the backdrops.

## Stockists

Search for `<h3>Stockists</h3>`. It currently says partners are being confirmed. When
you have your first stores, replace that paragraph with a list:

```html
<ul>
  <li>Erewhon — Silver Lake</li>
  <li>Lassens — Los Feliz</li>
</ul>
```

## Colours

Every colour is defined once, at the top of the `<style>` block under `:root`.

| Variable | Used for |
|---|---|
| `--cobalt` | Brand blue: the hero, buttons, headings |
| `--paper` / `--paper-warm` | The two light grounds |
| `--ink` | Near-black navy: body text and the dark sections |
| `--gold` | Warm accent |
| `--gold-on-cobalt` | A lighter gold used **only** for gold text on blue or dark grounds. It is lighter on purpose so the text stays readable — do not replace it with `--gold` |
| `--mist` | The muted neutral for secondary text |
| `--rust` | Coral, used sparingly |

## The signup form

Front-end only right now: it validates and confirms, but sends nothing anywhere.
Before launch, connect it:

- **Klaviyo / Mailchimp**: replace the `<form id="notify">` block with their embed code.
- **Keep this design**: add `action="https://…"` and `method="POST"` to the `<form>` tag
  using a form service (Formspree, Basin, Netlify Forms), then delete the
  `e.preventDefault();` line in the small script below it.

The page carries `<meta name="robots" content="noindex, nofollow">` so it cannot be
found in search. **Remove that line only after the form actually sends** — otherwise a
real customer signs up and you never see it.

## Before launch, also

- Delete the notice bar at the top: the `<p class="demo">…</p>` line.
- Add a real contact email in the footer.
- Bring the photography local (see above) so the page does not depend on a CDN.

## Things worth not breaking

- The scroll story is driven by the height of `.track` (`520vh`). Shorter speeds the
  sequence up, longer slows it down. Below roughly `320vh` the panels start to flick.
- Anyone with "reduce motion" enabled in their OS gets a static, stacked version of the
  whole story automatically. That lives in the `@media (prefers-reduced-motion: reduce)`
  block. Leave it in — it is also what makes the page readable if the animation ever
  fails to start.
- `anime.umd.min.js` must sit next to `index.html`. If you move it, update the
  `<script src="…">` line.
- Images carry `width` and `height` attributes so the page does not jump while they
  load. If you swap a photo for one with a different shape, update those two numbers.
