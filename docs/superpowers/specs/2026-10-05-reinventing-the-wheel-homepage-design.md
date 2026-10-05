# Reinventing the Wheel — Project Homepage Design

## What this is

"Reinventing the Wheel" is the umbrella project/brand this homepage represents — a deliberate pushback against modern app monetization: no subscriptions, no freemium tiers, no account requirements, no user-data tracking. Just apps that are free and actually work. The first (and currently only) app under this umbrella is **Setoff** (setoff.at), a free offline-first trip-packing app built from the founder's own 8-year personal packing spreadsheet.

Future apps will be sourced from three places: (1) paid apps the founder has personally replaced with their own workarounds, (2) underperforming free tools, (3) requests from other people. This is explicitly meant to be an ongoing, growing portfolio — not a one-off landing page for a single product.

This spec defines **reinventingthewheel.app** — the project's own home base, separate from and linking out to each individual app's own site.

## Scope decisions

Resolved via brainstorming with the user before this design was written:

1. **Primary job: credibility + home base, not lead capture.** The page exists so Setoff (and future apps) have a real parent brand behind them. Visitors land here, understand the philosophy, click through to whichever app they came for. No email signup, no "join the waitlist" mechanism — deliberately low-pressure, consistent with the project's own anti-dark-pattern philosophy.
2. **Distinct visual identity from Setoff**, not a reskin. This page is the parent; each app (Setoff included) keeps its own brand identity. A "toolkit/workshop" direction, cooler and more systematic than Setoff's warm amber-on-cream, with a restrained literal nod to the "wheel" in the name (a thin technical-line wheel/spoke motif, not a cartoon logo).
3. **Direct, plainspoken tone.** States the philosophy plainly — no subscriptions, no accounts, built because the founder needed it — without over-explaining or performing humility. Closest in register to Setoff's own "why this exists" section.
4. **Plain static HTML, no build step.** Same pattern as Setoff's own `index.html` marketing shell: inline `<style>`, no framework, no dependencies, deploys to Vercel as-is. Matches the project's own low-maintenance portfolio strategy; if the suite grows to 5+ apps with real interactive needs later, upgrading to a real build pipeline then is cheap and reversible.
5. **New, independent repo and Vercel project** (not folded into Setoff's repo), since this page is meant to outlive and outgrow any single app in the suite.
6. **Nothing to collect, so no privacy/terms pages.** Unlike Setoff (which handles real user accounts and trip data), this page has no forms, no accounts, no analytics, no tracking of any kind — genuinely nothing to disclose. Said plainly in the footer as a small, honest flourish that walks the page's own talk.

## 1. Content structure

- **Hero** — "Reinventing the Wheel" wordmark, a short, direct mission statement (one or two sentences) stating the philosophy plainly. The thin wheel/spoke line-art motif sits behind this section as the page's one distinctive visual signature.
- **Portfolio** — Setoff listed as app #1: name, one-line tagline, link out to setoff.at. Framed as the first entry in a growing list, not a lonely orphan — a simple "what's next" note underneath signals more are coming, built the same way, without naming anything unannounced.
- **Why this exists** — the manifesto, stated plainly: no subscriptions, no accounts, no tracking, built because the founder was tired of paying for or fighting with worse alternatives. Mirrors the structure of Setoff's own "why this exists" section, but speaking for the whole suite rather than one app.
- **How apps get picked** — the three sourcing criteria from the philosophy: apps the founder has personally replaced with their own workarounds, underperforming free tools, and requests from other people. Since "requests from others" is one of the three, this section is also the natural, low-pressure home for a plain `mailto:` link ("got an idea? tell me") — not a form, consistent with scope decision #1.
- **Footer** — contact (the same `mailto:` link), a link back to Setoff, the "no tracking, nothing collected" line from scope decision #6, and standard site meta (year, domain).

## 2. Visual identity

A cooler, more systematic "toolkit" direction than Setoff's warm amber-on-cream — deliberately distinct so the parent brand doesn't visually compete with each app's own identity.

**Color** (light theme; dark theme mirrors Setoff's own light/dark token pattern — redefine the same named tokens under `prefers-color-scheme: dark` rather than hand-picking unrelated dark colors):
- `--bg`: cool paper white, `hsl(210 20% 97%)`
- `--fg`: near-black ink, `hsl(220 20% 12%)`
- `--card`: pure white, `hsl(0 0% 100%)`
- `--muted`: cool grey, `hsl(215 10% 45%)`
- `--border`: `hsl(210 15% 88%)`
- `--accent`: confident petrol/teal, `hsl(190 75% 32%)` — a completely different hue family from Setoff's amber (30–40°); reads as "tool" rather than "travel"
- `--accent-fg`: white

**Type:**
- Headings and body: **Archivo** (confident grotesk, distinct from Setoff's Geist)
- Labels, eyebrows, status badges, footer meta: **IBM Plex Mono** — same structural role-split as Setoff's Geist/Geist Mono pairing (prose face vs. technical/label face), but different actual typefaces so the two sites read as siblings in spirit, not reskins of each other

**Layout:** clean single-column sections, same general rhythm as Setoff's page (alternating section backgrounds, generous whitespace) — but centered on the wheel/spoke motif as the one deliberate visual flourish, kept thin-lined and low-opacity so it reads as a technical diagram, not a logo mascot.

## 3. Technical & deployment plan

- **Repo:** new directory `side-hustle-apps/reinventing-the-wheel`, sibling to `trip-packing-app`, git-initialized with local author `jspiliot@gmail.com` set explicitly (Setoff's own deploy history has one real incident where the machine's global git email broke Vercel's GitHub-integration auto-deploy — same precaution applies here).
- **Hosting:** new GitHub repo under the `jspkiel` account, new Vercel project (GitHub-integrated, auto-deploy on push to `main`), `reinventingthewheel.app` DNS pointed at it the same way `setoff.at` was (A record for the apex domain, CNAME for `www`, both verified against GoDaddy's actual nameserver setup rather than assumed).
- **Site:** a single self-contained `index.html` — inline `<style>`, no external build step, no JS dependencies beyond what's needed for things like a mobile nav toggle if one turns out to be necessary. A hand-authored inline SVG for the wheel/spoke motif, reused for the favicon.
- **No testing infrastructure** — there's no app logic here, just markup and copy; verification is a build-free visual check (local file open + a live Playwright pass against the deployed site) rather than a test suite.

## Open questions

None — all scope decisions were resolved during brainstorming before this spec was written.
