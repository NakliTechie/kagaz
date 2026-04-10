# Kagaz

काग़ज़ — *paper.*

A browser-native personal site builder. One HTML file. No accounts. No servers. No data leaving your device.

**[→ Try it live](https://kagaz.naklitechie.com/)**

## What it does

Pick a combination — a layout × a colour palette × a typography pairing — fill in the blanks, and Kagaz hands you a deployable static site.

- **15 layouts.** Monolith, Atelier, Index, Card, Salon, Split, Marquee, Tile, Dossier, Terminal, Frame, Letter, Newspaper, Poster, Manifesto. Each one is a distinct visual posture for a different kind of person — the writer, the curator, the gallerist, the hacker, the polemicist.
- **240 colour palettes** across 22 families. Japan, China, India (North/West/East/South/Kashmir/Tribal/Sarees), Mexico, Morocco, Iran, Scandinavia, West Africa, Italy, Russia, Bauhaus, Brutalism, Memphis, Cyberpunk, Vaporwave, Chernobyl. Every palette has a story and a 7-slot contract — body, panel, ink, brand, action, ok, row — so any palette works with any layout.
- **8 typography pairings.** System, Editorial, Classical, Humanist, Geometric, Typewriter, Didone, Old-style. Web-safe and system fonts only — zero webfont fetches, zero external requests.
- **57 curated combinations.** Pamphleteer (Manifesto + Kajal + Classical), Couturier (Marquee + Zhusha + Didone), Replicant (Terminal + Blade Runner + Typewriter), and many more — each one a different tone of voice you can step into in one click.

## How to use

1. Open the live URL above (or serve `index.html` from any static server).
2. Pick a combination, fill the slots, save your `.kagaz` file (a portable zip you keep on your own disk).
3. When you're happy, click **Export site** — Kagaz produces a static folder you can drag straight into Cloudflare Pages, Netlify, GitHub Pages, or any static host.

The file format is open and documented. Your `.kagaz` file is just a zip with a `project.json` inside. You can read it, edit it by hand, version-control it, sync it across devices yourself — Kagaz never gets between you and your content.

## Why

Most "site builders" are SaaS subscriptions. You pay every month for what is, structurally, a text editor and a deployment pipeline bundled with hosting. Kagaz takes the editor and the deployment pipeline and gives them to you as a single HTML file. Hosting is free and yours to choose. The monthly fee disappears.

Beyond the economics, three things matter:

- **Privacy.** Your content never leaves your browser. There is no telemetry, no analytics, no "we may use your content to improve our service." The exported site is pure static HTML — no JavaScript, no tracking, no third-party requests.
- **Portability.** The `.kagaz` file is yours. The exported site is yours. If Kagaz disappears tomorrow, you still have your work and a deployable copy of your website. Nothing about the format requires Kagaz to keep existing.
- **Taste.** The 240 palettes and 15 layouts are not generic SaaS chrome. Each one is a deliberate point on a map of visual cultures — from Edo merchant ledgers to Bauhaus posters to Kashmiri pheran turquoise — that most personal-site builders ignore.

## Architecture

Single HTML file. No build step. No package manager. No dependencies you install — JSZip is lazy-loaded from the jsdelivr CDN the first time you save or export, and cached after that.

Everything else is inlined: 240 palettes, 15 layout render functions, 8 typographies, 57 combinations, the full slot vocabulary, 14 baked-in social icons, and the export pipeline that walks the project, renders each page through the layout, wraps it in an HTML shell with inlined CSS variables, drops referenced assets into an `assets/` folder, and embeds the source `.kagaz` alongside so the user always has both the editable file and the deployable site.

The output of `Export site` is a zip containing:

```
my-site.zip
├── index.html         (and about.html, work.html, etc. for multi-page layouts)
├── assets/            (only the images actually referenced in your content)
├── favicon.png        (auto-generated from your avatar, if you set one)
└── source.kagaz       (your editable source file, dropped in alongside)
```

## Status

**v1 — shipped.** The full editor is live. All three build phases are complete:

- **Engine** — 15 layout render functions, 240 palettes, 8 typographies, 57 curated combinations, `.kagaz` save/load, static export pipeline.
- **Editor UI** — Choose screen (57 combination cards, search, layout filter), Fill form with image drop zones, list editors with reorder and paste-from-CSV, links editor with 14 auto-detected icons, page tabs with add/remove, axis pickers to swap layout/palette/typography non-destructively, live preview, localStorage autosave.
- **Polish** — plain-English form labels, layout story modals (click the `i` on any card), Skip link for instant Architect default, open existing project from the Choose screen, multi-page layout renders.

## Run locally

```bash
python3 -m http.server 8080
# open http://localhost:8080/
```

That's it. No `npm install`, no `node_modules`, no build step.

## Part of NakliTechie

Kagaz is one of a series of browser-native tools published under the [NakliTechie](https://naklitechie.github.io/) banner. The thesis: most software you pay a monthly fee for is just an editor and a deployment pipeline bundled with hosting. Take any two of those away and the third becomes free. So we're taking them away, one tool at a time.

## License

[MIT](LICENSE) — © 2026 Chirag Patnaik
