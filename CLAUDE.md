# Fruit Stand site — project context

This repo is the **fruitstand.dev website**, rebuilt on [Mintlify](https://mintlify.com)
(docs-as-code). It replaces the previous site, which was hosted on **Pagy** (a
no-code builder that was weak for technical docs — no sidebar, search, or code
highlighting). The whole site (home, dataset docs, contact, privacy) now lives
here as MDX.

## Design tokens (match the old fruitstand.dev exactly)

- Font: **Figtree** (headings + body)
- Accent color: **`#f04242`** (red)
- Background white, text black; pill-shaped buttons (`border-radius: 100px`)
- Logo: `logo/logo.svg` (a 2000×2000 raster-in-SVG mark; also used as favicon)

## Structure

```
docs.json                 # theme, colors, nav, footer, "Try for Free" button
index.mdx                 # home / landing (hero + CTA + dataset cards)
contact.mdx
privacy-policy.mdx        # ported word-for-word from the live Pagy page
datasets/
  fred-series.mdx
  earnings-call-transcripts.mdx
logo/logo.svg  favicon.svg  images/og.png   # brand assets (self-hosted, no Pagy CDN)
```

Snowflake marketplace listing (the "Try for Free" target):
`https://app.snowflake.com/marketplace/listing/GZTYZ40XYU5`

## Preview / deploy

- Local preview: `npx mint dev` → http://localhost:3000
- Deploy: push to a GitHub repo, install the Mintlify GitHub App on it
  (auto-deploys on push), then set `fruitstand.dev` as a custom domain in the
  Mintlify dashboard + add the CNAME at the DNS provider. Cut DNS off Pagy last.

## Outstanding / to verify

- **Privacy policy** has two boilerplate lists that couldn't be scraped cleanly
  and need checking against the original: the "We may share Your personal
  information…" list (omitted) and the "Other legal requirements" list (filled
  with standard Privacy Policy Generator wording).
- **Contact page** is just an email link. A real form needs an embed
  (Tally/Formspree) — Mintlify has no native form component.

## Possible next work

The docs currently mirror the old marketing-level content. They could be
substantially deepened with **schema/table definitions and SQL examples** mined
from the actual data pipelines, which live in a **separate repo**:
`~/Documents/mango` — Dagster assets in `quickstart_snowflake/{fred,earning_calls,fund_returns}/`
and dbt models in `snowflake_dbt/models/`. (There is also a **fund_returns**
dataset in that repo with no doc page here yet.)
