# RALLY landing page — how to make content updates

The whole page is one file: `index.html`. No build step, no framework, no npm install.
Open it in any text editor, change the text, save, re-upload. That is the entire workflow.

## The three things you will change most

### 1. Headline and intro copy
Search for `<h1>`. The headline and the paragraph under it (`class="lede"`) sit together
near the top of the file, inside `<section class="hero">`.

### 2. The four scroll-story panels
Search for `<div class="panel"`. There are four, numbered 01 to 04 in the `<span class="num">`
line. Each one has a heading (`<h2>`) and one or two paragraphs. Edit the words between the tags
and leave the tags alone.

To reorder them, move the whole `<div class="panel">…</div>` block. To add a fifth, copy an
existing block, paste it after the last one, and change `0.235` to `0.19` in the script near the
bottom (search for `var BAND`) so the scroll splits five ways instead of four.

### 3. Stockists
Search for `<h3>Stockists</h3>`. Right now it says retail partners are being confirmed. When you
have your first stores, replace that paragraph with a list:

```html
<ul>
  <li>Erewhon — Silver Lake</li>
  <li>Lassens — Los Feliz</li>
</ul>
```

## Colors
All brand colors are defined once, at the very top of the `<style>` block, under `:root`.
Change a hex there and it updates everywhere on the page.

| Variable | Used for |
|---|---|
| `--cobalt` | Brand blue: headings, buttons, the sky |
| `--cream` | Page background and card backgrounds |
| `--yellow` | Accent: the eyebrow line, tags, highlighted words |
| `--coral` | Decorative coral (progress bar, bottle label) |
| `--coral-ink` | The darker coral used for any coral *text* or button — it is darker on purpose so the text stays readable. Do not swap it for the bright coral. |
| `--sea` / `--sand` | The illustrated beach |

## The signup form
The form is currently front-end only — it validates and shows a confirmation, but nothing is sent
anywhere. Before this goes live it needs to be connected to whatever list you use.

- **Klaviyo / Mailchimp**: paste their embed code in place of the `<form id="notify">` block.
- **Keep this design, just make it send**: add `action="https://…"` and `method="POST"` to the
  `<form>` tag using a form service (Formspree, Basin, Netlify Forms), then delete the
  `e.preventDefault();` line in the script at the bottom.

Until that is done the page carries a `noindex` tag so it cannot be found in search. **Remove the
`<meta name="robots" content="noindex, nofollow">` line only after the form actually works** —
otherwise a real customer can sign up and you will never see it.

## Before launch, also
- Delete the grey demo notice at the top of the page: the `<p class="demo-bar">…</p>` line.
- Swap the illustrated bottle for your product photography if you prefer — the bottle is inline
  SVG inside `<div class="roller">`. Replace it with `<img src="bottle.png" alt="RALLY king
  coconut water">` and the rolling animation will still work on the image.
- Fill in a real contact email in the footer.
- Add your Instagram handle if it changes (search for `instagram.com`).

## Things worth not breaking
- The scroll animation reads the height of `.story-track` (`460vh` in the CSS). Making it shorter
  speeds the roll up; longer slows it down. Do not set it below about `300vh` or the panels flick.
- Anyone with "reduce motion" turned on in their OS gets a static stacked version automatically.
  That is handled by the `@media (prefers-reduced-motion: reduce)` block. Leave it in.
- Every image and icon on the page is inline SVG or CSS, which is why it loads instantly. Adding
  large photos is fine, but add `loading="lazy"` and set `width`/`height` on them.
