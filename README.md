# creagh.law — website

Source for the Creagh Law website: a single static page hosted free on Cloudflare Pages.
No framework, no build step. Editing the HTML and committing is all it takes to deploy.

## Files

| File | What it is |
|---|---|
| `index.html` | The entire site — markup, styles, and scripts in one self-contained file |
| `tom-creagh-portrait.jpg` | Portrait used in the About section (referenced by relative path) |
| `favicon.png` | Browser tab icon (the "c." brand mark) |
| `apple-touch-icon.png` | Home-screen icon for iOS when the site is saved to a phone |
| `fonts/` | Self-hosted web fonts — Urbanist (headings) and IBM Plex Sans (body) |
| `robots.txt` | Tells search engines they may index the whole site |
| `README.md` | This file |

The logo wordmarks shown on the page are **not** in this repo — they're served from a
separate `brandingassets` repo via the jsDelivr CDN (see "Where things live" below).

## How to edit

1. Open `index.html` here on GitHub, click the pencil icon, edit, and commit
   (or upload a replacement file with the same name).
2. Cloudflare Pages detects the commit and redeploys automatically — live in about 10 seconds.
3. To preview before it hits the real domain, check the staging URL (below) — it always
   reflects the latest commit.

When editing copy, change the words *between* the HTML tags and leave the tags themselves.
Example: in `<h1>Counsel that meets you <span class="accent">outside business hours.</span></h1>`,
edit the words and keep the `<h1>`, `<span>`, and closing tags intact. GitHub keeps every
previous version, so a bad edit can always be reverted.

## Fonts

Fonts are self-hosted in `fonts/` rather than loaded from Google Fonts, so they load reliably
everywhere (no third-party CDN, nothing for ad/privacy blockers to break, and faster). If you
ever change a font, drop the new `.woff2` files in `fonts/` and update the `@font-face` blocks
near the top of `index.html`.

- **Headings:** Urbanist (weights 500, 600, 700)
- **Body:** IBM Plex Sans (weights 400, 500, 600)

> If you deploy a new `index.html` that references font files, make sure the matching files are
> in `fonts/` in the same commit — otherwise the page falls back to a system font.

## Where things live

| Thing | Where | Notes |
|---|---|---|
| Hosting | Cloudflare Pages | Connected to this repo; auto-deploys on commit |
| Live site | `https://www.creagh.law` (and `creagh.law` via redirect) | |
| Staging / preview | `https://creagh-law-site.pages.dev` | Always reflects the latest commit |
| DNS | Squarespace | Website records only; email DNS untouched |
| Email | Microsoft 365 | Unaffected by the website — separate DNS records |
| Domain registration | Squarespace | |
| Logo / wordmark files | separate `brandingassets` repo, served via jsDelivr | Logo changes happen there, not here |
| HTTPS certificate | Automatic via Cloudflare | Nothing to manage |

## Notes

- Editing this site does not touch email in any way — the email DNS records live separately
  at Squarespace and aren't referenced here.
- The site is plain HTML/CSS/JS on purpose: fast, durable, and easy to edit without tooling.
