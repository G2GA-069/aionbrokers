# G2G Advisory · Broker Intelligence

Universal M&A advisor matchmaker for G2G Advisory — 400+ UK corporate-finance advisors and business brokers, scored and ranked against any deal in real time, with the data signal behind every recommendation.

**Live:** https://g2g-broker-intel.whatimade.app

## What it does

Two modes, one dataset.

**Matchmaker.** Enter a deal — Enterprise Value, sector, geography, deal type — and the engine ranks the 400+ firms instantly. Each card shows the match score (0-100), a colour-coded breakdown across the four scoring axes (EV overlap /40, sector fit /35, tier match /15, geography /10), a one-line plain-English rationale, and a data-confidence badge (Verified / Researched / Auto-listed) so you know how much of the underlying record is independently corroborated.

**Browse.** The full database, filterable by firm type, pipeline status, SaaS-focus score, email presence and FCA registration. CRM state (status, notes) persists in `localStorage`.

## Architecture

Single self-contained `index.html` plus the icon set. No build step, no dependencies beyond Google Fonts (Playfair Display + Inter + JetBrains Mono). Deployable to GitHub Pages, Netlify, S3, or any static host.

## Local use

```bash
git clone https://github.com/G2GA-069/aionbrokers.git
cd aionbrokers
# Open index.html in a browser
```

## Changing the password

```bash
echo -n "YourNewPassword" | sha256sum
```

Replace `PW_HASH` in `index.html` with the SHA-256 hex digest.

## Scoring engine

```
total = EV-overlap (0-40) + sector-fit (0-35) + tier-match (0-15) + geography (0-10)
```

- **EV overlap** rewards firms whose stated deal range *contains* the query. A firm covering £20m-£750m gets full credit for a £200m deal.
- **Sector fit** scans the firm's `sector`, `notes`, `saas_kw` and `name` fields against curated keyword sets per sector. Technology uses the firm's SaaS score directly.
- **Tier match** maps firm type (bulge / elite / upper-MM / tech specialist / CF boutique / accountancy / broker) to deal size with empirically-tuned weights.
- **Geography** prefers London / national / international networks per query.

Firms below a 30-point threshold are hidden. Top results show one-line rationales like *"Signals strong energy/oil & gas coverage · deal range £100m-£5bn+ brackets your size."*

## Fee estimator

Lehman-style sliding scale (5% / 4% / 3% / 2% / 1% across £10m / £15m / £25m / £50m / £100m brackets) with type multiplier (bulge ×1.8 down to broker ×0.5), sector premium (tech / energy / cross-border each +10-15%), and per-type minimum floor. Displayed as a low-high band on every card and in the detail-panel live calculator.

## Data confidence

Each firm is scored on six signals: lead contact verification, team-page scrape, confirmed-email count, analyst notes length, Companies House record, team-size on file. Surfaced as a 3-level badge with a hover popover showing the underlying checks.

---

Built for G2G Advisory · London corporate finance & M&A.
