# partypaper.co.uk

Single-page holding site for **Party & Paper** — handcrafted party favours,
party bags and gift wrap.

Plain HTML and CSS. No build step, no dependencies, no JavaScript.

```
index.html                  the page
styles.css                  brand tokens + layout
assets/
  logo-party-and-paper-*.png  wordmark, pink and white colourways
  favicon*, apple-touch-icon  the brand heart, cropped from the logo
  og-party-and-paper.png      1200x630 social card (white on pink)
  fonts/                      self-hosted Grandstander, Montserrat, Caveat
vercel.json                 cache headers + security headers
robots.txt, sitemap.xml
```

## Local preview

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

## Brand rules this site follows

From the brand board (v1). Worth re-reading before changing anything visual.

| Token | Hex | Use |
|---|---|---|
| Party Pink | `#F6396C` | Logo, buttons, accents. **Never tint or shade it.** |
| Blush | `#F6E4EB` | Default background |
| Sugar Paper | `#FFF8F4` | Cards and text panels |
| Ribbon Plum | `#4A1F33` | All body text — never black |
| Sherbet | `#FFC44D` | Small doses only (the "opening soon" badge) |
| Kraft | `#C8A17E` | The real colour of the bags and tape |

Rough colour balance: 55% blush, 25% paper, 15% pink, 5% accents.

- **Grandstander** (700) — headlines only, never a whole paragraph.
- **Montserrat** (400/600/700) — body, labels, buttons.
- **Caveat** (500) — handwriting, one line at a time.

Logo: pink-on-light is the default, minimum 180px wide on screen, and it never
sits on a busy pattern — hence the Candy Stripe appears only as a thin ribbon
at the top. The heart is used on its own as the favicon, which the brand board
explicitly allows.

Voice: warm, quick, never twee. Useful thing first. Short sentences. One
exclamation mark per page at most — this page uses none.

## Accessibility

Checked in Chromium at 1440px and 390px:

- All text meets WCAG AA. Body copy on Blush is 11.2:1; the lowest ratio on the
  page is the white-on-pink button at 3.67:1, which is why it is set at 19px/700
  — that puts it in WCAG's "large text" bracket, where the threshold is 3:1.
- One `h1`, sequential headings, `lang="en-GB"`, alt text on the logo.
- Visible 3px focus ring on every interactive element; tap targets ≥44px.
- Honours `prefers-reduced-motion` and `prefers-contrast: more`.
- No horizontal scroll at either width.

## Deploying to Vercel

The repo is a static site, so Vercel needs no framework preset and no build
command. Import the repo, leave the build settings empty, deploy.

For `partypaper.co.uk`, add both the apex and `www` in
**Project → Settings → Domains**, then point DNS at Vercel. If DNS is on
Cloudflare, the records are:

| Type | Name | Value | Proxy |
|---|---|---|---|
| `A` | `@` | `76.76.21.21` | DNS only (grey cloud) |
| `CNAME` | `www` | `cname.vercel-dns.com` | DNS only (grey cloud) |

Vercel shows the exact values to use on the Domains screen — trust those over
this table if they differ. The proxy must stay off, or Vercel cannot issue the
TLS certificate.
