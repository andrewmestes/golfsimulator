# golfsimulator

Concept one-page site for a portable golf simulator business based in Loveland,
Colorado — built as a pitch draft, not a finished brand.

One file, no build step. `index.html` is the whole site: fonts come from Google
Fonts, everything else is inline. Open it in a browser and it works.

## Renaming the business

The brand name appears in exactly **three** places, by design:

1. `var BRAND = 'Pin High';` near the top of the `<script>` block — this fills
   every `[data-brand]` span on the page.
2. The `<title>` tag.
3. The Open Graph / Twitter / JSON-LD blocks in `<head>`.

`Pin High` is a placeholder. It's a real golf term (a shot that finishes level
with the flag) that also nods to Colorado altitude. It has **not** been checked
for trademark or domain availability.

## What is still placeholder

| Thing | Status |
| --- | --- |
| Business name | Placeholder — see above |
| Pricing ($895 / $1,450 / $2,600) | Benchmarked just under Denver market rates. Sample only. |
| Phone `(970) 555-0142` | Reserved fictional range. Not a real number. |
| Email / domain `pinhighgolf.co` | Not registered or verified |
| Testimonials | Explicitly labelled in-page as written examples, not real reviews |
| Photography | None yet — the hero is a generated ball-flight canvas, not a photo |

The `CONCEPT DRAFT` bar at the top of the page is deliberate. It keeps the
client from reading the sample pricing as a commitment. Remove it when the real
numbers land.

## Search engines are blocked on purpose

`<meta name="robots" content="noindex, nofollow">` in `index.html`, reinforced
by an `X-Robots-Tag` header in `vercel.json`. A draft carrying a placeholder
brand should not get indexed. **Remove both** when this becomes the real site.

## The two pieces worth keeping

- **Hero ball-flight canvas** — draws a live launch-monitor trace with ball
  speed, launch angle, spin and carry counting up, cycling through four clubs.
  Honours `prefers-reduced-motion` by drawing one static arc instead.
- **"Will it fit?" checker** — sliders plus venue presets that answer the
  question every event planner asks first. Five honest verdict states,
  including "your room is too tight, we'd park the trailer outside."

## Deploying

Vercel builds this straight from `main` — static, no build command, no install
step. Pushing to `main` deploys.

## Known gaps

- The booking form is not wired to anything. It says so when submitted.
- No Open Graph image. Add a 1200×630 PNG and an `og:image` tag once there are
  photos of the actual rig — link previews are currently text-only.
- Below 900px the anchor nav collapses to just the CTA button. Fine for a
  one-pager; wants a drawer if the site grows.
