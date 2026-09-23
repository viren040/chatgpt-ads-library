# ChatGPT Ads research report

Generated from the verified first-party library at 2026-09-23T09:25:00Z. Rates use complete-panel observations, including both ad and zero-ad outcomes. Positive-only reviewed migrations contribute to the advertiser directory but not appearance rates.

## Current evidence

- **104** approved advertiser families and **106** displayed advertiser labels
- **279** approved paid placements across **206** creative variants
- **166 of 896** complete-panel turns contained an approved paid placement (18.5%)
- **166** rate-eligible placements and **113** reviewed positive-only placements

## What worked

| Prompt category | Turns | Ad turns | Rate | Advertisers | Evidence |
|---|---:|---:|---:|---:|---|
| Corporate travel | 155 | 74 | 47.7% | 19 | established |
| Honeymoon packages | 9 | 6 | 66.7% | 4 | directional |
| Intercity buses | 29 | 13 | 44.8% | 5 | established |
| Luxury perfume gifts | 9 | 4 | 44.4% | 4 | directional |
| Citrus perfume | 11 | 4 | 36.4% | 3 | directional |
| Fragrance layering | 8 | 3 | 37.5% | 3 | directional |
| Vacation rentals | 141 | 26 | 18.4% | 7 | established |
| Paint services | 33 | 9 | 27.3% | 2 | established |
| Fleet tracking | 8 | 2 | 25.0% | 2 | directional |
| Coworking | 12 | 4 | 33.3% | 1 | directional |

Corporate travel is the clearest established high-competition prompt category in this dataset. Travel and perfume subcategories also produced repeated paid signals, but small perfume samples remain directional.

After a paid placement appeared, deeper turns retained a placement in 51 of 53 transitions (96.2%). These turns are useful for creative and advertiser variation, but they should not replace breadth when the goal is discovering new brands.

## What did not work

A more purchase-specific follow-up rescued 38 of 485 prior zero-ad turns (7.8%). The yield fell with depth, so zero-ad conversations should receive one follow-up before capacity returns to breadth.

Mature zero-signal categories currently excluded from the next evidence-led allocation: **None yet**.

Prompts that merely mention a product or brand do not establish an ad. The collector counts only paid cards visibly marked “Ad” or “Sponsored” and tied to the completed assistant turn.

## How to increase useful speed

1. Keep one in-flight turn per signed-in account and respect the configured account spacing.
2. Run supervised workers through the persistent loopback coordinator API so claim and evidence writes do not start a Python process for every event.
3. Add verified account capacity across independent laptop shards; more tabs in one profile do not add quota.
4. Give one purchase-specific rescue follow-up to a zero-ad seed, then return capacity to breadth if it remains zero.
5. Continue ad-bearing conversations when the objective is creative variation; prioritize breadth and promising categories when the objective is new advertisers.
6. Keep the 20% breadth / 20% promising / 60% adaptive allocation and rebalance it from reviewed evidence, not pending detections.
7. Measure a complete uninterrupted 60-minute browser window before converting a short run into daily capacity.

An offline coordinator validation on 2026-09-23 ran 20 concurrent workers through 200 complete
lifecycles and 600 HTTP requests in 2.387 seconds, with every observation persisted and no write
failures or abandoned leases. This validates the per-laptop control plane only; browser response
time, account spacing, and platform availability still determine collection throughput.

## Most frequently observed advertisers

- **TwixAir LLC** — 25 placements, 14 creatives; Travel and leisure,Corporate travel,Honeymoon packages
- **Trip.com/flights** — 17 placements, 5 creatives; Corporate travel,Honeymoon packages
- **DRIVEU MOBILITY SOLUTIONS PRIVATE LIMITED** — 13 placements, 6 creatives; Vacation rentals,Intercity buses,Corporate travel,Fleet tracking
- **Homerun Retail Private Limited** — 12 placements, 7 creatives; Commercial discovery,Electronics,Trade delivery,Travel luggage,Vacation rentals,Corporate travel,Paint services,Bathroom fittings
- **trivago** — 11 placements, 9 creatives; Travel and leisure,Vacation rentals
- **Zoho Corporation** — 11 placements, 4 creatives; Help desk software,Corporate travel
- **MakeMyTrip** — 10 placements, 6 creatives; Domestic flights,Vacation rentals,Corporate travel,Honeymoon packages
- **HSBC - Credit Cards** — 9 placements, 4 creatives; Vacation rentals,Corporate travel
- **Agoda Company Pte. Ltd.** — 8 placements, 7 creatives; Commercial discovery,Travel and leisure,Vacation rentals,Weekend resorts
- **abhibus** — 7 placements, 6 creatives; Commercial discovery,Travel and leisure,Logistics,Intercity buses
- **The Man Company** — 7 placements, 7 creatives; Beauty and personal care,Rose perfume
- **Birla Opus** — 6 placements, 1 creatives; Paint services
- **Nestle Professional** — 6 placements, 2 creatives; Card terminals,Office leasing,Coworking
- **Wikka Potions for Aromatherapy** — 6 placements, 3 creatives; Beauty and personal care,Body mists,Citrus perfume,Fragrance layering
- **Duke & D’Or** — 5 placements, 5 creatives; Beauty and personal care,Fragrances,Fragrance layering,Citrus perfume
- **Nexxbase Marketing Pvt. Ltd** — 5 placements, 5 creatives; Travel and leisure,Business productivity,Business hotels,Intercity buses,Fleet tracking
- **Insurte** — 4 placements, 4 creatives; Travel and leisure,Corporate travel
- **ixigo** — 4 placements, 4 creatives; Travel and leisure,Flight booking
- **UJ PALLAZZIO - Business Class Luxury Hotel** — 4 placements, 2 creatives; Intercity buses,Corporate travel
- **Guest Reservations** — 3 placements, 3 creatives; Travel and leisure

The complete advertiser directory is in [`observed-advertisers.csv`](./observed-advertisers.csv). Every approved placement, prompt, answer, format, disclosure, creative, and screenshot reference is in [`placements.csv`](./placements.csv) and [`library.json`](./library.json).

## Workflow now in use

1. Seed a fixed breadth panel and keep it separate from adaptive discovery.
2. Assign a conversation to one account for its full lifetime.
3. Capture the completed answer, paid disclosure, advertiser, creative, screenshot, and timestamp without clicking the placement.
4. Import immutable evidence bundles into the central library.
5. Require human review for every new advertiser identity. Exact-pixel inheritance and deterministic OCR may approve only already-known identities under their strict checks.
6. Publish approved evidence only; keep pending and rejected detections out of public counts.
7. Compare categories with complete-panel denominators and label samples below 20 observations as exploratory or directional.

## Limits

This library proves that a paid placement appeared in the captured session at the recorded time. It does not prove campaign spend, bids, conversions, targeting settings, universal availability, or that a campaign is active now. Account tier, login state, market, language, surface, viewport, prompt wording, and conversation stage can change what appears.
