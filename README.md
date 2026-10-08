# B&S LUXURY × Selected Developers — the developer experience

A standalone HTML presentation for strategic conversations with selected luxury
developers. No build step, no internet needed: fonts, photos, video and logos are all
inside `assets/`. It evolves the David Deza / Brown Harris Stevens deck: same design
system, same navigation, a different strategic conversation.

## Run it

- Double-click `index.html` (works from the file system), **or**
- `node serve.mjs` and open <http://localhost:4500> (recommended for the video).

Press **F** for full screen before you start.

## Driving the deck

| Action | Keys / gestures |
| --- | --- |
| Next step or slide | → · ↓ · Space · Enter · Page Down · click (right 80 % of the screen) · swipe left · scroll down |
| Previous | ← · ↑ · Backspace · Page Up · click (left 20 %) · swipe right · scroll up |
| First / last slide | Home / End |
| Full screen | F (or the corner icon bottom-right) |
| Slide index | I (or the menu icon top-right) |
| Jump to a chapter | the five lines on the right edge (hover shows the name) |

Pacing: every reveal delay is scaled by `SPEED` at the top of the deck's step bookkeeping (`0.6` now; `1` is the original, slower timing).

The deck has 15 screens in six chapters. Left and right arrows sit at the edges on every screen size (bottom corners on a phone); they move one whole slide, fully revealed, while the keys step through the reveals. Most slides have several **steps**: pressing →
reveals the next idea on the same slide before moving on, so you can pace each point
verbally. Going back lands on the previous slide fully revealed. `#7` in the URL opens
slide 7 directly. The deck holds indefinitely on any slide: ambient motion loops, nothing
auto-advances (on a phone, steps play by themselves).

## The narrative

| # | Chapter | Screens |
| --- | --- | --- |
| 00 | Opening | Cover with the project mark · Today (the agenda: five lines) |
| 01 | Who we are | Biz & Style ("One platform. Three divisions." as an org chart: Biz & Style, the holding, on top, branching to Commerce · Advisory · Luxury (a tree on a phone), Luxury marked as our focus, the positioning statement under a gold rule) · The ecosystem · Our objective · On the map (The Real Deal, a statement of intent; investing ahead of the business in the team and in the digital infrastructure) · Growing progressively, selecting the top (the agent ring) |
| 02 | The market · the gap | One screen: 170+ new developments and 60,000+ realtors in Miami alone, then: everyone promotes everything · the influencer approach · we don't follow it · we select what we believe in · a limited number of projects, a deeper commitment · when we believe, we go all in |
| 03 | The engines | Two engines (the headline on top: "Two engines. One growth system."; the offline luxury ecosystem and the online in-house acquisition as two panels joined by B&S Luxury, stacked on a phone) · Digital lead generation (01 the tech, built in-house · 02 the people, converted in-house, with the developers named: PMG, Terra, Continuum) · International reach (the Biz & Style world map: dotted coastlines, routes from Miami to Los Angeles, Toronto, New York, Mexico City, Santo Domingo, Panama, Bogotá, Lima, São Paulo, London, Paris, Milan, Madrid, Dubai, Singapore) · One integrated ecosystem (luxury ecosystem, lead generation, broker community, international reach around the project) |
| 04 | The partnership | Already committed (the project's own rendering: three tiles — website built, campaigns running, resources committed — then "It's already happening. How fast can we go together?") · How it works — three steps: 01 how to start, a temporary advance of the amount you select, which activates the full infrastructure; 02 for your peace of mind, we match it with our own capital in pure media (directly to the Google Ads and Meta platforms, not to us); 03 you recover it from the sales, at the first commission. Three columns on a wide screen, a vertical timeline on a phone |
| 05 | Next step | "We already committed." then B&S LUXURY × the project mark and "Let's accelerate. Together." on the project's rendering |

The money appears only in chapter 05, after the value has been established. The two
commitments are always shown as two separate pools: the developer's partnership
commitment funds the ecosystem / business-development activation; B&S Luxury's own
capital funds the dedicated digital media. No slide adds them into one budget.

## Personalising it for a developer

Everything that changes from one developer to the next lives in the `PROJECT` object at
the top of the `<script>` in `index.html`:

| Key | What it drives |
| --- | --- |
| `name`, `shortName` | cover, the integrated ecosystem, "Integrated", "Already committed", next step. `shortName` (≤ 16 characters) is used inside the circles |
| `developer`, `location` | cover, "Already committed" |
| `partner`, `partnerLogo` | optional sales & marketing partner (none now): its mark beside the project mark on the cover, its name beside the developer |
| `logo` | the project mark on "Next step" (a dark mark on a transparent SVG or PNG; it is inverted to white) |
| `currency`, `partnership`, `match` | the amounts on "How it works" (default `100` and `100`, an illustrative unit; the counters animate to whatever you set) |
| `event` | optional invitation line on "Next step" |
| `images`, `priceRange`, `valueProposition`, `whySelected`, `commissionPct`, `exampleUnitPrice`, `contact` | reserved for optional screens not in the current sequence |

The current values are set for Cipriani Residences Miami, Brickell (Mast Capital).
The rendering behind "Already committed" and "Next step" is `ciprianiBrickell` in `ASSETS`;
the project mark is `assets/logos/cipriani-residences.png`.

Two ways to switch developer without editing the deck:

- URL parameters for a quick run: `index.html?project=The%20Residences&developer=Acme%20Development&partnership=25K&match=25K#1`
- A small script before the deck loads: `<script>window.PROJECT_OVERRIDES = { name: '…', … }</script>` placed right before the main `<script>` in `index.html`, or copied into a per-developer HTML file that includes the deck.

All figures are illustrative and the legal line on the economic slides says so. Change the
figures, keep the line.

## Replacing images and logos

Every visual is resolved from the `ASSETS` map at the top of the `<script>`. Change a path
there and the deck follows; nothing else references files.

| Key | Used on | File now |
| --- | --- | --- |
| `coverVideo` / `coverPoster` | cover | `assets/photos/miami-hero.mp4` / `.jpg` |
| `southOfFifth` | "170+ new developments" | `assets/photos/south-of-fifth.webp` |
| `logoBns` / `logoBnsDark` | chrome, cover | `assets/logos/bns-luxury-miami-*.png` |
| `logoBizStyle` / `logoBizStyleDark` | chrome, organisation chart | `assets/logos/bizandstyle-*.png` |
| `logoRealDeal` | The Real Deal | `assets/logos/the-real-deal.png` |
| `brickell`, `miami`, `fisherIsland`, `miamiBeach`, `partner…` | not used in the current sequence; kept for the optional screens | `assets/…` |

Photos are graded dark in CSS (`.media__img` filter and `.media__veil`), so bright daytime
shots still read as cinematic. Landscape, at least 1920 px wide, is ideal. Partner marks
are black-on-white files rendered with a multiply blend on the ivory slide; a transparent
or white-background logo works best.

## Review helpers

`index.html?nofx=1&full=1#12` opens slide 12 with every step revealed and motion frozen,
counters landed — useful for screenshots or proofreading. `&step=2` instead of `full=1`
opens a specific step.

## Deploying

The repository deploys to Netlify straight from GitHub `main` (see `netlify.toml`: no build step,
the root is the site). Push to `main` and Netlify publishes; the `preview` branch is for work in
progress. 

Share previews: the `<title>` and the Open Graph tags in the `<head>` name the deck "B&S Luxury × Cipriani Residences" and point WhatsApp / iMessage at `assets/photos/share.jpg` (1200×630). The `og:image` URL is absolute and currently assumes `https://bnsxcipriani.netlify.app`; change it to the final domain once Netlify assigns one.
