# golfsimulator

Concept one-page site for an **inflatable** golf simulator rental business based in
Loveland, Colorado — built as a pitch draft, not a finished brand.

One file, no build step. `index.html` is the whole site: fonts come from Google
Fonts, the rig illustration is inline SVG, everything else is inline. Four JPEGs
in `img/`. Open it in a browser and it works.

## Renaming the business

The brand name appears in exactly **three** places, by design:

1. `var BRAND = 'Pin High';` near the top of the `<script>` block — this fills
   every `[data-brand]` span on the page.
2. The `<title>` tag.
3. The Open Graph / Twitter tags in `<head>`.

`Pin High` is a placeholder. It's a real golf term (a shot finishing level with
the flag) that also nods to Colorado altitude. It has **not** been checked for
trademark or domain availability.

## It's one unit, not two

Earlier drafts modelled this on Dryvebox — a trailer *plus* an indoor pop-up.
That's wrong for an inflatable. There is **one** unit; it goes indoors or
outdoors. If you find copy implying two formats, it's a leftover.

Specs used throughout, from what the category actually advertises:

| | |
| --- | --- |
| Footprint | 15′ W × 12′ D |
| Height | 10′ ideal, 9′ workable (irons and wedges only) |
| Power | One 110V outlet — the blower runs continuously |
| Setup | 45 min up, 30 min down |

## Pricing is benchmarked to the inflatable tier

Inflatable rentals advertise roughly **$150–250/hr with a 3–4 hour minimum**.
Trailer operators (Dryvebox et al.) charge $350–500/hr. An earlier draft priced
this at $298/hr, which put it in the wrong category. Current sample rates —
$595/3hr, $895/5hr, $1,595/day — sit inside the inflatable band. Still sample
numbers; the real ones are the client's to set.

## The rig illustration

`<symbol id="rig">` near the top of `<body>`, used twice (hero and the setup
figure) via `<use href="#rig">`. Edit it once.

**Why an illustration and not a photo:** there is no photograph of an inflatable
golf simulator in any free-licensed library. Openverse returns nothing; Pexels
"inflatable screen" is all outdoor cinemas. Competitors' own photos are
copyrighted and are also *their* equipment. The illustration is legally clean and
clearly reads as a diagram rather than a fake photo. It carries a caption saying
the client's rig photos replace it.

Three things stop it reading as a television, and they matter if you edit it:

- **The golfer.** Scale is what makes it a room you stand in rather than a screen
  you watch. It paints *after* the frame and mat — draw it earlier and the tubes
  cover its legs.
- **The projector and light cone.** Says projection rig, not TV.
- **The screen fills the whole back wall.** A screen inset in a bezel reads as a
  monitor. No bezel.

## Photography — where it came from

Four images, all from **Pexels** under the [Pexels License](https://www.pexels.com/license/):
free for commercial use, no attribution required. Committed to `img/` rather than
hotlinked.

| File | Pexels ID |
| --- | --- |
| `ev-corporate.jpg` | 6405751 |
| `ev-wedding.jpg` | 10408275 |
| `ev-fundraiser.jpg` | 6405786 |
| `ev-private.jpg` | 6405661 |

**No colour cast on people.** An earlier draft ran these through a turf-green
`mix-blend-mode: color` duotone to unify four different shoots. It unified them
and it also made everyone look ill. Green now lives on surfaces — bands, chips,
bullets, the segmented control — and never on skin.

Three golf-course photos were used and then dropped when the site moved to
inflatable-specific imagery: `bay.jpg` (31212256), `fairway.jpg` (6256594),
`turf.jpg` (34710413). Re-fetch by ID if wanted.

**Caveat for launch:** the Pexels License permits identifiable people
commercially, but strangers beside event copy edges toward implied endorsement.
Fine for a pitch; replace with the client's own event photos before this goes
live. That is the highest-value asset they can bring.

## The course ticker

Two marquee rows pairing a famous course with an ordinary venue — "St Andrews at
the company retreat", "Royal Troon in the church gym". The joke is the collision.

**Every course named is one that actually exists in simulator libraries**
(TrackMan / Foresight license Pebble Beach, St Andrews, Whistling Straits,
Kiawah, Torrey Pines, Bandon Dunes, Spyglass, Harbour Town, Bethpage, Valderrama,
Wolf Creek). **Augusta National is deliberately absent** — it is in no simulator's
library, and the club is famously aggressive about its trademarks. Don't add it.

Rows pause on hover and stop entirely under `prefers-reduced-motion`.

## Colour and weight

Paper-first: `--paper #F7F5EE` is the page. Dark is held back for three moments —
the hero, the comparison band, and the booking block plus footer. An earlier
draft was dark throughout and read as heavy.

`--turf #14663D` carries the category. `--apricot #D9661F` is CTAs, the accent
word in the headline, and the draft notice. `--signal` chartreuse is data-only:
launch-monitor numerals and the stat-band units. It is not a brand colour.

## Content notes that are easy to get wrong

- **Do not claim a five-month golf season.** An earlier draft leaned on "Colorado
  golf is a five-month sport." It isn't — with sun, people play here year round.
  The band now argues throughput instead: a foursome is 4 players over 5 hours,
  the simulator is 50+ players in one.
- The headline avoids "indoors." The unit works outside too, so anything implying
  indoor-only is wrong.

## Search engines are blocked on purpose

`<meta name="robots" content="noindex, nofollow">` in `index.html`, reinforced by
an `X-Robots-Tag` header in `vercel.json`. A draft with a placeholder brand and a
fictional phone number should not get indexed. **Remove both** when it goes live.

## Deploying

Vercel builds this straight from `main` — static, no build command, no install
step. Pushing to `main` deploys.

## Known gaps

- The booking form is not wired to anything. It says so when submitted.
- No Open Graph image, so link previews are text-only. Add a 1200×630 PNG and an
  `og:image` tag once there are photos of the real rig.
- Below 860px the anchor nav collapses to just the CTA button. Fine for a
  one-pager; wants a drawer if the site grows.
- Phone `(970) 555-0142` is a reserved fictional number; `pinhighgolf.co` is not
  registered.
