# Carlos Garage Door Services — demo site

Unapproved demo built by Grand Nash Studio. Single self-contained `index.html`, no build step.

Direction: gallery style No. 12 Masculine, reinterpreted. Condensed uppercase (Oswald,
inlined as base64 so the page makes zero external requests), galvanized steel ground with a
brushed grain and soft door seams, his logo's red as the accent, and a consistent shallow angled
cut taken from the curve where a garage door track turns. The steel ground is the chrome
sectional door in his own logo; the red is his logo red; the phone block copies his logo's
phone bar (black ground, white numerals, red rule). Hazard yellow is reserved for genuine
warnings and demo caveats only, never as a brand colour.

TODO: drop the real logo PNG into the header slot (currently a labelled placeholder).

Section order is by urgency, not by marketing convention: the symptom triage opens the page,
price is answered second, then who shows up, proof, work, and services last for the visitor
who is browsing rather than locked out.

Deploy: drag this folder into Netlify.

Before this becomes a real, paid, approved site:

- Replace the sample pricing table with Carlos's real numbers, or remove the section.
- Replace the six `Pictures go here` blocks with Carlos's own photos.
- Verify the six review quotes against the Google listing (transcribed from a screenshot).
- Wire the request form to a real handler. It is front-end only right now.
- Remove `<meta name="robots" content="noindex, nofollow">`, delete `robots.txt`, and remove the demo bar at the top of the page and the demo note in the form confirmation.
