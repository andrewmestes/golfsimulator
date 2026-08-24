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

## The business model, stated plainly

They own **one** inflatable simulator. They are hired to bring it, set it up, run
it for the event, and take it away. They do **not** sell or lease systems, and
there is no second format — earlier drafts copied Dryvebox's trailer-plus-pop-up
model, which is wrong here. Any copy implying two units, a purchase, or an
unstaffed drop-off is a leftover and should go.

The single mention of "trailer" (in the setup section) is deliberate contrast
against trailer operators, not a description of this rig.

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

## There is no rig illustration any more

A hand-drawn SVG of the unit was tried twice — first as a white front-facing
frame, then as a black three-quarter cube built from the client's reference
photo. Both were cut. At hero size the drawn golfer and flat panels read as
amateur work, which is worse than no image.

The hero now uses `bay.jpg`, a real photograph of a golf simulator.

**It is a rigid bay, not an inflatable.** That is a knowing compromise, and the
setup figure carries a caption saying so. The search was exhausted first:
Openverse has nothing for "inflatable golf simulator"; Pexels "inflatable
screen" is all outdoor cinemas; the only on-concept public results (a US Army
"Outdoor Golf Simulator" set) are **CC BY-NC-ND**, which forbids both commercial
use and cropping. Competitors' photos are copyrighted and are their equipment.

So: a real, well-shot, commercially-licensed simulator beats a drawing that
looks fake. Replace it the moment the client photographs their own unit — that
single photo is the highest-value asset they can bring.

## Photography — where it came from

Four images, all from **Pexels** under the [Pexels License](https://www.pexels.com/license/):
free for commercial use, no attribution required. Committed to `img/` rather than
hotlinked.

| File | Pexels ID | Where |
| --- | --- | --- |
| `bay.jpg` | 31212256 | Hero |
| `turf.jpg` | 34710413 | Setup figure |
| `ev-corporate.jpg` | 6405751 | Events |
| `ev-wedding.jpg` | 10408275 | Events |
| `ev-fundraiser.jpg` | 6405786 | Events |
| `ev-private.jpg` | 6405661 | Events |

**No colour cast on people.** An earlier draft ran these through a turf-green
`mix-blend-mode: color` duotone to unify four different shoots. It unified them
and it also made everyone look ill. Green now lives on surfaces — bands, chips,
bullets, the segmented control — and never on skin.

`fairway.jpg` (6256594) was used and dropped — a golfer on a course sells golf,
not this service. Re-fetch by ID if wanted.

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

## The copy is written customer-first

StoryBrand rules apply: the host is the hero, we are the guide. The headline is
**"Be the reason nobody leaves early."** — what the buyer gets, not what we own.
An earlier draft ran "A golf course that fits in a van", which is a fact about
our equipment and gives a prospective client nothing.

Same test elsewhere: the setup section is "Nothing for you to set up", not "One
unit, inside or out". If a heading describes the product rather than the
customer's outcome, rewrite it.

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
