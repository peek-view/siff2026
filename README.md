# siff2026
SIFF Film Festival 2026

# SIFF 2026 Conflict Guide

An unofficial planner for the **Seattle International Film Festival** (May 7–17, 2026). Browse all 210 screenings across 6 venues, see at a glance which films overlap, mark what you want to see, and remember what you don't.

[**→ View live**](https://YOUR-USERNAME.github.io/REPO-NAME/) <!-- replace with your URL -->

---

## What it does

- **Sees the whole festival on one page.** All 11 days, 210 screenings, 114 films, 6 venues — laid out by day with conflict groups visualized inline so you can tell at a glance which films overlap.
- **Tracks your picks.** Tap the ★ on any film to save it. Picks persist across browser sessions via `localStorage`. Open the **My Picks** tab to see your selections grouped by day, with conflict warnings if you've starred two films that overlap.
- **Tracks what you've ruled out.** Tap the ⊘ to mark a film as "not interested" — all of its screenings get dimmed across the schedule, so you remember next time you scroll past it. Toggle a filter to hide them entirely.
- **Surfaces programmer recommendations.** Every film picked by one of SIFF's 20 festival programmers shows a cyan "★ N picks" badge on its card. Expand the card to read each programmer's personal blurb. Filter the schedule to show only programmer-recommended films.
- **Links straight to tickets.** Every card has a "Tickets & info ↗" button that opens the film's official SIFF page where you can buy tickets and confirm the latest showtime.
- **Handles multiple showings.** When a film screens more than once, each card shows a "1 / 2" badge so you know which showing you're looking at, and the expanded detail lists all of them with the current one marked.

## Why I built it

The official SIFF program lists 200+ screenings across a dense 11-day grid. Trying to figure out which of your favorites conflict — and across multiple venues at multiple times — is exhausting from the printed program or a long PDF. This page collapses everything into one scrollable view designed around the question that actually matters: *what am I going to see, and what do I have to skip to see it?*

## Tech & architecture

- **One self-contained HTML file** (~190 KB). No build step, no dependencies, no backend. Open it directly from disk or host it anywhere static. Works offline once loaded.
- **Vanilla JS, vanilla CSS.** No React, no frameworks. Performance is excellent for a page of this size and the file stays small enough to share by AirDrop or email.
- **Persistent state** via `localStorage` — picks and "not interested" marks survive across browser sessions on the same device. (No cross-device sync; that would require a server.)
- **Source data** extracted from the official SIFF 2026 master schedule grid (Excel format). Programmer picks scraped from the per-programmer pages on siff.net.

## Hosting it yourself

The whole thing is one HTML file. Drop it anywhere static:

- **GitHub Pages**: rename to `index.html`, push to a repo, enable Pages in Settings.
- **Netlify Drop**: drag the file onto [app.netlify.com/drop](https://app.netlify.com/drop). Done in under a minute.
- **Cloudflare Pages**: similar idea, free tier.
- **Any web server**: it's just one HTML file.

If you just want to share with a few friends, AirDrop or email the file directly — it works offline.

## Caveats

- **Not affiliated with SIFF.** This is a fan project. The official source of truth for showtimes, ticket availability, and last-minute changes is always [siff.net](https://www.siff.net/festival).
- **Schedule snapshot.** The data was extracted in late April 2026. Films get added, rescheduled, or sell out as the festival approaches. The "Tickets & info ↗" link on each card always takes you to SIFF's authoritative page.
- **Library screenings limited.** The grid this is built from doesn't include the Seattle Central Library venue, except for Reservation Redemption (added manually). If you spot other Library-only screenings missing, they need to be patched in.
- **No cross-device sync.** Your picks stay on the browser you set them on. If you star a film on your laptop, it won't appear on your phone.

## Features in detail

### Viewing the schedule
- Each day shows screenings in time order, grouped into "conflict slots" — pink-bordered groups where you have to pick one because the films overlap.
- Click any film card to expand it and see synopsis, credits, country/year, premiere status, the trailer button (opens YouTube search), and the SIFF tickets link.
- Filter by venue (Uptown / Downtown / Film Center / PacSci / Paramount) using the pills at the top.
- Filter to show only programmer-recommended films (88 of 114 films have at least one).
- Filter to hide films you've marked "not interested."

### My Picks tab
- The first tab is **★ My Picks** — your saved films grouped by day, with conflict warnings if any of them overlap each other.
- "Clear all picks" button with confirmation, so you can reset for a different planning session.
- Same for "Clear all not-interested marks."

### Conflict logic
Two screenings are in the same conflict slot if and only if they pairwise overlap with every other film in the group — i.e. you genuinely have to pick one. Films that only share time with *some* members of a group don't get falsely grouped (this is the [interval graph clique](https://en.wikipedia.org/wiki/Interval_graph) definition, not transitive chaining).

## Credits

- **Schedule, films, programmer's picks**: [Seattle International Film Festival](https://www.siff.net) (used with attribution; not endorsed by SIFF).
- **Built with**: ☕ and a lot of squinting at PDFs.

## License

The code is free to fork and adapt. The schedule data and programmer's picks belong to SIFF.
