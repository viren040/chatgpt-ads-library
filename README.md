# ChatGPT Ads Library

A searchable, evidence-first library of paid placements observed in signed-in ChatGPT sessions.

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
- placement-level and creative-level views;
- reviewed screenshots and evidence context; and
- category ad-appearance and competition metrics from complete experiment panels.

Denominator-based rates exclude the historical positive-only migration so older ads cannot inflate
category appearance rates.

## Verify the release

From the collector repository, run:

```bash
ads-library-verify /path/to/this/repository
```

The verifier checks the manifest, public dataset, approval boundary, credential-field exclusions,
standalone interface, and every evidence screenshot. Browser profiles, cookies, passwords, session
tokens, and local databases are never included in this repository.
