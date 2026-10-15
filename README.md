# Rebecca Harris Advisory

A single-page expert-brand website for **Rebecca Harris** — provider-network &
credentialing advisory. Clean, healthcare-professional, mobile-first, built on the
HumanData Design System v4 (same tokens, type, and components) under her own name.

- **Live (GitHub Pages):** set after first deploy — see *Deploy* below.
- **Intended domain:** `rebeccaharrisadvisory.com` (not yet registered).

## What's here

```
index.html          The whole site (DS v4 stylesheet embedded inline — self-contained)
img/favicon.svg     "RH" accent mark
img/og.png          1200×630 social share card (LinkedIn/Slack/iMessage preview)
robots.txt
sitemap.xml
.github/workflows/deploy.yml   CI/CD → GitHub Pages
```

It's a static page — **no build step**. Edit `index.html` and push.

## Deploy (CI/CD)

Push to `main`. GitHub Actions publishes the repo to GitHub Pages. The workflow
runs a sanity check first (og image present, canonical present, the honest
career-record caveat intact), then deploys. `workflow_dispatch` re-runs a deploy
without a commit.

One-time setup on the repo: **Settings → Pages → Build and deployment → Source:
GitHub Actions.** (The `gh` commands used to create this repo already set this.)

## Custom domain (`rebeccaharrisadvisory.com`)

Do this once the domain is registered:

1. Add a `CNAME` file at the repo root containing one line: `rebeccaharrisadvisory.com`
   (and commit it), **or** set it under Settings → Pages → Custom domain.
2. At the registrar, point DNS at GitHub Pages:
   - Apex `@`: four A records → `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153` (and the matching AAAA records if you
     want IPv6).
   - `www`: a CNAME → `designresearchgroup.github.io`.
3. Wait for DNS, then tick **Enforce HTTPS** in Settings → Pages.
4. Set up email for `rebecca@rebeccaharrisadvisory.com` (the booking address on the
   page) at the registrar/host so the CTA actually receives mail.

Until the domain is live, the site serves from the GitHub Pages URL and every
link/preview still works.

## Design system

The embedded stylesheet is HumanData DS v4 verbatim (source of truth:
`humandata.id/ds`). Keep brand changes in the small page-specific `<style>` block
at the top of `index.html`, not in the DS block, so the system stays one source.

## Honesty note (important)

The track-record figures (~300 ASCs/SNFs, ~15k behavioral-health panel, 300+
hospitals, 2,000+ providers) are **Rebecca's personal career experience**, framed
that way on the page and in the footer — not a company's past performance, and not
a promise of results. Don't add outcome/percentage claims without data to back them.
