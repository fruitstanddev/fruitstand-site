# Fruit Stand — Mintlify site

The full fruitstand.dev site (home, datasets docs, contact, privacy) as a
Mintlify project. Themed to match the current site: **Figtree** font,
**`#f04242`** accent, white/black, and the existing logo.

## Structure

```
docs.json                         # theme, colors, nav, footer
index.mdx                         # home / landing (hero + CTA)
contact.mdx
privacy-policy.mdx
datasets/
  fred-series.mdx
  earnings-call-transcripts.mdx
logo/logo.svg                     # brand mark (also used as favicon)
favicon.svg
images/og.png                     # social share image
```

## Preview locally

```bash
npm i -g mint      # or: npx mint dev
cd fruitstand-site
mint dev           # serves http://localhost:3000
```

## Go live (the steps only you can do)

1. **Create the repo.** Push this `fruitstand-site/` folder to its own GitHub
   repo (Mintlify deploys from a repo root, so make `docs.json` the top-level
   file — see "Splitting out" below).
2. **Sign up at [mintlify.com](https://mintlify.com)** and install the Mintlify
   GitHub App, pointing it at that repo. Every push auto-deploys.
3. **Custom domain.** In the Mintlify dashboard → Settings → Domain, set
   `fruitstand.dev` (or `docs.fruitstand.dev`). Add the CNAME record it gives
   you at your DNS provider.
4. **Move DNS off Pagy** only after the Mintlify deploy looks right, so there's
   no downtime. Keep Pagy up until then.

## Splitting out into its own repo

Mintlify expects `docs.json` at the repo root. From this folder:

```bash
cd fruitstand-site
git init && git add . && git commit -m "Fruit Stand site on Mintlify"
gh repo create fruitstand-site --private --source=. --push
```

## Notes / to verify

- **Privacy policy:** ported word-for-word from the live page. Two boilerplate
  spots could not be scraped cleanly and should be checked against your
  original: (a) the "We may share Your personal information in the following
  situations" list (omitted — the source rendered it empty), and (b) the
  "Other legal requirements" bullet list (filled with the standard Privacy
  Policy Generator wording). Confirm both match your intended policy.
- **Contact form:** the current site only lists an email, so this is an email
  link. If you want a real form, embed one (Tally/Formspree) — Mintlify has no
  native form component.
- **Logo:** the Pagy SVG is a 2000×2000 raster-in-SVG mark; it doubles as the
  favicon. Swap in a dedicated wordmark/favicon later if you want.
