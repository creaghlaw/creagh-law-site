# creagh.law — website

Source for the Creagh Law website: a single static page hosted free on
Cloudflare Pages. No framework, no build step. Editing the HTML and
committing is all it takes to deploy.

## Files

|File                     |What it is                                                              |
|-------------------------|------------------------------------------------------------------------|
|`index.html`             |The entire site — markup, styles, and scripts in one self-contained file|
|`tom-creagh-portrait.jpg`|Portrait used in the About section (referenced by relative path)        |
|`favicon.png`            |Browser tab icon (the “c.” brand mark)                                  |
|`apple-touch-icon.png`   |Home-screen icon for iOS when the site is saved to a phone              |
|`fonts/`                 |Self-hosted web fonts — Urbanist (headings) and Figtree (body)          |
|`robots.txt`             |Tells search engines they may index the whole site                      |
|`README.md`              |This file                                                               |

The logo wordmarks shown on the page are **not** in this repo — they’re
served from a separate `brandingassets` repo via the jsDelivr CDN (see
“Where things live” below).

## How to edit

1. Open `index.html` here on GitHub, click the pencil icon, edit, and commit
   (or upload a replacement file with the same name).
1. Cloudflare Pages detects the commit and redeploys automatically — live in
   about 10 seconds.
1. To preview before it hits the real domain, check the staging URL (below) —
   it always reflects the latest commit.

When editing copy, change the words *between* the HTML tags and leave the
tags themselves. GitHub keeps every previous version, so a bad edit can
always be reverted.

## Dark mode

The site has a dark theme that follows the visitor’s device setting
automatically (`prefers-color-scheme`) — there is no toggle and nothing to
configure. Phones and computers set to dark mode get a midnight-navy version
of the site; everyone else sees the light version. To preview the dark
theme, switch your device appearance (Mac: System Settings → Appearance;
iPhone: Settings → Display & Brightness) or use browser DevTools → Rendering
→ “Emulate CSS prefers-color-scheme”.

All dark-mode colors live in one `@media (prefers-color-scheme: dark)` block
near the bottom of the styles in `index.html`. The logo swaps to the
reversed wordmark automatically via `<picture>` elements. Design details,
tokens, and the accessibility audit are documented in `DARK_MODE_SPEC.md`
(kept outside this repo with the brand documents).

## Fonts

Fonts are self-hosted in `fonts/` rather than loaded from Google Fonts, so
they load reliably everywhere. If you ever change a font, drop the new
`.woff2` files in `fonts/` and update the `@font-face` blocks near the top
of `index.html`.

- **Headings:** Urbanist (weights 500, 600, 700)
- **Body:** Figtree (weights 400, 500, 600)

> If you deploy a new `index.html` that references font files, make sure the
> matching files are in `fonts/` in the same commit — otherwise the page
> falls back to a system font. (The old IBM Plex Sans files can be deleted
> from `fonts/` if they’re still there; nothing references them.)

## Where things live

|Thing                |Where                                                   |Notes                                                                                             |
|---------------------|--------------------------------------------------------|--------------------------------------------------------------------------------------------------|
|Hosting              |Cloudflare Pages                                        |Connected to this repo; auto-deploys on commit                                                    |
|Live site            |`https://www.creagh.law` (and `creagh.law` via redirect)|                                                                                                  |
|Staging / preview    |`https://creagh-law-site.pages.dev`                     |Always reflects the latest commit                                                                 |
|DNS                  |GoDaddy                                                 |`www` CNAME → Cloudflare Pages; apex forwards to `www` via GoDaddy Forwarding; email DNS untouched|
|Email                |Microsoft 365                                           |Separate DNS records at GoDaddy — unaffected by the website                                       |
|Domain registration  |GoDaddy                                                 |                                                                                                  |
|Logo / wordmark files|separate `brandingassets` repo, served via jsDelivr     |Logo changes happen there, not here                                                               |
|HTTPS certificate    |Automatic via Cloudflare                                |Nothing to manage                                                                                 |

## Notes

- Editing this site does not touch email in any way — the email DNS records
  live separately at GoDaddy and aren’t referenced here.
- The site is plain HTML/CSS/JS on purpose: fast, durable, and easy to edit
  without tooling.