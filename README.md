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
- a visually reviewed embedded or content-addressed HTTPS screenshot; and
- content hashes recorded in `manifest.json`.

Organic brand mentions, historical candidate lists, incomplete responses, rejected detections,
and unreviewed cards are excluded. A record proves one observed placement at a specific time. It
does not reveal campaign spend, bids, targeting settings, conversions, or current campaign status.

## Explore the data

The standalone interface supports:

- full-text search across advertisers, creative copy, prompts, and prompt categories;
- prompt-category and advertiser filters;
- filtering each placement by complete-panel or reviewed positive-only provenance;
- verified CSV and JSON downloads for independent analysis;
- a complete-panel prompt outcome CSV containing ad and zero-ad turns;
- placement-level and creative-level views;
- reviewed screenshots and evidence context; and
- prompt-category ad-appearance and competition metrics from complete experiment panels; and
- ad-appearance rates by seed, zero-rescue, and ad-deepening conversation stages.

Every placement carries an `evidence_design` and `rate_eligible` field. A `complete_panel` record
comes from a panel that preserves both ad and zero-ad turns, so it may contribute to appearance
rates. A `reviewed_positive_only` record proves a visually reviewed appearance, but its source did
not preserve the corresponding zero-ad turns. It remains searchable and is excluded from every
denominator-based rate.

Every placement also carries `review_method`. `human_visual` means a reviewer inspected that
observation. `exact_visual_inheritance` means its screenshot bytes or decoded RGBA pixels,
advertiser, creative ID, disclosure, and format exactly matched a previously approved placement.
Its review note identifies that source. Lossless metadata or compression may differ; any changed
decoded pixel or creative field remains pending for human review.

The `category` and `industry` fields describe the prompt context in which the placement appeared.
They do not classify the advertiser or creative. This meaning is also recorded in the
`field_semantics` object in `library.json`.

`placements.csv` contains one row per approved placement with the observation time, advertiser,
creative copy, prompt category, evidence design, rate eligibility, prompt, completed answer, creative ID,
and content-addressed screenshot.
`library.json` additionally contains advertiser summaries and complete-panel experiment denominators.
The site initially loads `catalog-summary.json` with aggregate insights and twelve recent
placements. Hash-stable `catalog/*.json` shards load only for search, filtering, or more results.
Full answers and review notes live in verified `details/*.json` shards and load only when evidence
context is opened.

`prompt-observations.csv` contains one row per settled complete-panel turn, including zero-ad turns.
It records the generated prompt, prompt category, cohort, pseudonymous conversation ID, turn index,
conversation branch, reviewed ad outcome, paid-unit count, creative count, and advertisers. It does
not contain account slots, conversation URLs, answers, browser profiles, or credentials.

## Verify the release

From the collector repository, run:

```bash
ads-library-verify /path/to/this/repository
```

The verifier checks the manifest, public dataset, approval boundary, credential-field exclusions,
standalone interface, and every embedded evidence screenshot. For external evidence it verifies
the exact HTTPS base URL and content-addressed filename; the publishing host separately hash-checks
every object during its idempotent store sync. Browser profiles, cookies, passwords, session
tokens, account-slot labels, ChatGPT conversation URLs, and local databases are never included in
this repository.
