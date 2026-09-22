# ChatGPT Ads Library

A searchable, evidence-first library of paid placements observed in signed-in ChatGPT sessions.

**Browse the live library:** https://viren040.github.io/chatgpt-ads-library/

Open `index.html` through a static web server, or visit the GitHub Pages URL shown in this
repository's About section.

## Evidence boundary

Every published placement has:

- an explicit **Ad** or **Sponsored** disclosure;
- a visible advertiser identity;
- the prompt and completed assistant answer from the observed turn;
- a visually reviewed screenshot; and
- content hashes recorded in `manifest.json`.

Organic brand mentions, historical candidate lists, incomplete responses, rejected detections,
and unreviewed cards are excluded. A record proves one observed placement at a specific time. It
does not reveal campaign spend, bids, targeting settings, conversions, or current campaign status.

## Explore the data

The standalone interface supports:

- full-text search across advertisers, copy, prompts, answers, and categories;
- category and advertiser filters;
- filtering each placement by complete-panel or reviewed positive-only provenance;
- verified CSV and JSON downloads for independent analysis;
- placement-level and creative-level views;
- reviewed screenshots and evidence context; and
- category ad-appearance and competition metrics from complete experiment panels; and
- ad-appearance rates by seed, zero-rescue, and ad-deepening conversation stages.

Every placement carries an `evidence_design` and `rate_eligible` field. A `complete_panel` record
comes from a panel that preserves both ad and zero-ad turns, so it may contribute to appearance
rates. A `reviewed_positive_only` record proves a visually reviewed appearance, but its source did
not preserve the corresponding zero-ad turns. It remains searchable and is excluded from every
denominator-based rate.

`placements.csv` contains one row per approved placement with the observation time, advertiser,
creative copy, category, evidence design, rate eligibility, prompt, completed answer, creative ID,
and content-addressed screenshot.
`library.json` additionally contains advertiser summaries and complete-panel experiment denominators.

## Verify the release

From the collector repository, run:

```bash
ads-library-verify /path/to/this/repository
```

The verifier checks the manifest, public dataset, approval boundary, credential-field exclusions,
standalone interface, and every evidence screenshot. Browser profiles, cookies, passwords, session
tokens, and local databases are never included in this repository.
