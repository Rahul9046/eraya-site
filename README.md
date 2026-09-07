# eraya.app — holding page

The public page at [eraya.app](https://eraya.app) until the product opens.
Served by GitHub Pages from the `main` branch of this repo.

```
index.html    the whole page — markup, styles and the mark, inlined
favicon.svg   the approved Eraya mark, verbatim from the brand asset pack
CNAME         the custom domain GitHub Pages serves this on
.nojekyll     serve the files as they are; no Jekyll build
```

No build step, no dependencies, no framework. Open `index.html` and it renders.

## Why this is its own repo

The product lives in a separate monorepo. This page shares nothing with it: no
imports, no Supabase client, no API call. A holding page has to survive a broken
deploy, a migration, or a rotated key in the thing it is holding the door for,
and the cheapest way to guarantee that is to give it nothing to depend on.

The cost of that isolation is that the brand tokens in `<style>` are
**transcribed** from the product's brand documentation rather than imported. If
the palette or the mark is ever revised, this file must be updated by hand — it
will not follow along. Worth paying for a page that lives for a few weeks.

The mark was injected programmatically from `eraya-approved-favicon.svg` in the
brand asset pack, so it is byte-identical to the approved artwork rather than
redrawn.

## Editing it

Edit `index.html`, commit to `main`, push. GitHub Pages redeploys in about a
minute. There is nothing to build and nothing to install.

## There is no signup form

By design. A form needs somewhere to put the address, and that means a backend —
the exact coupling this page avoids. It offers `hello@eraya.app` instead. If a
real waitlist is wanted before launch, the honest options are a hosted form
(Tally, Formspree) or the product's own waitlist once it is live.

## Known gaps

- **No `og:image`.** Shared links preview as title and description on a plain
  card. That is deliberate — an `og:image` pointing at a file that is not there
  renders as an empty box, which is worse. To add one, commit a 1200x630 PNG and
  add `<meta property="og:image" content="https://eraya.app/og.png">`. Worth
  doing before the link is shared on WhatsApp, where the preview card carries
  most of the click.
- **No analytics.** Nothing is measured. Adding a privacy-respecting counter
  (Plausible, Fathom) is a one-line script if the traffic matters.

## When the product is ready

Repoint the `eraya.app` DNS at the product's host and archive this repo. Take
the `CNAME` file out of this repo first, or GitHub Pages will keep claiming the
domain and the two hosts will fight over it.
