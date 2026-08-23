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

## Photography — where it came from and what it cost

All seven images are from **Pexels**, under the [Pexels License](https://www.pexels.com/license/):
free for commercial use, modification allowed, no attribution required. They are
committed to `img/` rather than hotlinked, so nothing breaks if a URL moves.

| File | Pexels ID | What it is |
| --- | --- | --- |
| `bay.jpg` | 31212256 | A real golf simulator bay — hero background and The Bay card |
| `fairway.jpg` | 6256594 | Swing follow-through on a fairway — The Rig card and the season band |
| `turf.jpg` | 34710413 | Wedge and ball on hitting turf — booking section |
| `ev-corporate.jpg` | 6405751 | Colleagues toasting |
| `ev-wedding.jpg` | 10408275 | Indoor wedding reception |
| `ev-fundraiser.jpg` | 6405786 | Sparklers at an evening event |
| `ev-private.jpg` | 6405661 | Friends at an indoor party |

### Two honest caveats

**Free stock has almost no golf simulators in it.** `bay.jpg` is essentially the
only real simulator bay on Pexels — everything else returned by "golf simulator"
is putting mats, VR headsets and pool tables. A Topgolf bay photo was rejected
because the competitor's logo is visible on the console.

**Identifiable people in stock photos are a grey area on a commercial site.** The
Pexels License permits it, but showing strangers next to event copy edges toward
implied endorsement. Fine for a pitch draft; before this goes live it wants the
client's own event photos, which will be better anyway. That is the single
highest-value asset they can bring.

### The duotone is doing real work

The four event photos come from four different shoots. `.ev-img` gets
`grayscale(1)` and `.ev-duo` lays turf green over it with `mix-blend-mode: color`,
which forces them into one palette; hover relaxes both. Remove that treatment and
the cards immediately look like four unrelated stock photos.

Note `.band-duo` is deliberately lighter (0.4). A `color` blend preserves the
backdrop's luminosity, and the fairway shot is luminance-flat, so a heavy scrim
on top erases the image completely.

## Colour

Green carries the category, apricot only carries the energy. `--turf` (`#135E38`)
is used across whole surfaces — the stat band, the segmented control, bullets on
the light sections. `--apricot` is reserved for CTAs, the accent word in the hero
headline, and the draft notice.

The chartreuse `--signal` is data-only: launch-monitor numerals and the stat-band
units. It is not a brand colour and should not spread.

One trap already hit: `.specbar .spec p` and `.specbar .spec .big s` need the
extra class to out-specify the generic `.spec` rules further down the sheet.
Written as `.specbar .big s` they tie on specificity, lose on source order, and
silently put apricot on turf green at 2.82:1.

## Deploying

Vercel builds this straight from `main` — static, no build command, no install
step. Pushing to `main` deploys.

## Known gaps

- The booking form is not wired to anything. It says so when submitted.
- No Open Graph image. Add a 1200×630 PNG and an `og:image` tag once there are
  photos of the actual rig — link previews are currently text-only.
- Below 900px the anchor nav collapses to just the CTA button. Fine for a
  one-pager; wants a drawer if the site grows.
