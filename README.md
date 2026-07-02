# Margin Recovery OS

A zero-dependency MVP prototype for a hospitality margin recovery platform.

The product promise: **find recoverable dollars across vendor invoices, delivery payouts, labor, bar variance, comps/voids, menu cost drift, and rebates — then create the recovery workflow.**

## Run locally

```bash
python3 -m http.server 5173
# open http://localhost:5173
```

## What is included

- Executive recovery command center
- Recovery opportunities ranked by dollars, confidence, urgency, and owner
- Claim packet builder for vendor, delivery, rebate, labor, and bar leakage
- Recovery pipeline: Found -> Assigned -> In Review -> Submitted -> Recovered
- Category workspaces: vendor, delivery, labor, bar, menu, rebates
- Manual evidence upload placeholders
- Operator notes and approval workflow placeholders
- Mock hospitality data seeded for restaurants/bars/multi-unit operators

## Why zero-dependency

This repo is intentionally simple so Claude Code can pick it up fast, refactor it into React/Supabase, and preserve the product logic without dependency lock-in.

## Recommended next architecture

- Frontend: React + Vite or Next.js
- DB: Supabase Postgres
- Auth: Supabase Auth / Clerk
- Storage: Supabase Storage / S3
- Jobs: Inngest / Trigger.dev
- Integrations: POS, AP/invoice OCR, delivery payout CSV/API, labor, inventory, accounting
- AI: anomaly clustering, claim draft generation, evidence summarization, prioritization only

## Core wedge

Do not build a dashboard. Build a recovery queue that proves value in dollars.

First customer should be a 2-12 unit restaurant/bar group with fragmented vendor, delivery, labor, and closeout workflows.
